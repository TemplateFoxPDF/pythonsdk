# TemplateFox Python SDK

Official Python SDK for [TemplateFox](https://pdftemplateapi.com) - Generate PDFs from HTML templates via API.

[![PyPI version](https://badge.fury.io/py/templatefox.svg)](https://pypi.org/project/templatefox/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Installation

```bash
pip install templatefox
```

Or with poetry:

```bash
poetry add templatefox
```

## Quick Start

```python
from templatefox import ApiClient, Configuration
from templatefox.api import PDFApi
from templatefox.models import CreatePdfRequest

# Initialize the client
config = Configuration()
config.api_key['ApiKeyAuth'] = 'your-api-key'

with ApiClient(config) as client:
    api = PDFApi(client)

    # Generate a PDF
    response = api.create_pdf(
        CreatePdfRequest(
            template_id='YOUR_TEMPLATE_ID',
            data={
                'name': 'John Doe',
                'invoice_number': 'INV-001',
                'total_amount': 150.00,
            }
        )
    )

    print(f'PDF URL: {response.url}')
    print(f'Credits remaining: {response.credits_remaining}')
```

## Features

- **Template-based PDF generation** - Create templates with dynamic variables, generate PDFs with your data
- **Multiple export options** - Get a signed URL (default) or raw binary PDF
- **S3 integration** - Upload generated PDFs directly to your own S3-compatible storage
- **Type hints** - Full type annotations for IDE support

## API Methods

### PDF Generation

```python
from templatefox.models import CreatePdfRequest

# Generate PDF and get URL
response = api.create_pdf(
    CreatePdfRequest(
        template_id='TEMPLATE_ID',
        data={'name': 'John Doe'},
        export_type='url',       # 'url' or 'binary'
        expiration=86400,        # URL expiration in seconds (default: 24h)
        filename='invoice-001'   # Custom filename
    )
)
```

### Templates

```python
from templatefox.api import TemplatesApi

templates_api = TemplatesApi(client)

# List all templates
templates = templates_api.list_templates()
for template in templates.templates:
    print(f'{template.id}: {template.name}')

# Get template fields
fields = templates_api.get_template_fields(template_id='TEMPLATE_ID')
for field in fields:
    print(f'{field.key}: {field.type} (required: {field.required})')
```

### Account

```python
from templatefox.api import AccountApi

account_api = AccountApi(client)

# Get account info
account = account_api.get_account()
print(f'Credits: {account.credits}')
print(f'Email: {account.email}')

# List transactions
transactions = account_api.list_transactions(limit=100, offset=0)
for tx in transactions.transactions:
    print(f'{tx.transaction_type}: {tx.credits} credits')
```

### S3 Integration

```python
from templatefox.api import IntegrationsApi
from templatefox.models import S3ConfigRequest

integrations_api = IntegrationsApi(client)

# Save S3 configuration
integrations_api.save_s3_config(
    S3ConfigRequest(
        endpoint_url='https://s3.amazonaws.com',
        access_key_id='AKIAIOSFODNN7EXAMPLE',
        secret_access_key='your-secret-key',
        bucket_name='my-pdf-bucket',
        default_prefix='generated/pdfs/'
    )
)

# Test connection
test = integrations_api.test_s3_connection()
print(f'Connection: {"OK" if test.success else "Failed"}')
```

## Configuration

```python
from templatefox import Configuration

config = Configuration(
    host='https://api.pdftemplateapi.com',  # Default API URL
)
config.api_key['ApiKeyAuth'] = 'your-api-key'

# Or use environment variable
import os
config.api_key['ApiKeyAuth'] = os.environ.get('TEMPLATEFOX_API_KEY')
```

## Error Handling

```python
from templatefox.exceptions import ApiException

try:
    response = api.create_pdf(CreatePdfRequest(...))
except ApiException as e:
    if e.status == 402:
        print('Insufficient credits')
    elif e.status == 403:
        print('Access denied - check your API key')
    elif e.status == 404:
        print('Template not found')
    else:
        print(f'Error: {e.reason}')
```

## Async Support

```python
import asyncio
from templatefox import ApiClient, Configuration
from templatefox.api import PDFApi
from templatefox.models import CreatePdfRequest

async def generate_pdfs():
    config = Configuration()
    config.api_key['ApiKeyAuth'] = 'your-api-key'

    async with ApiClient(config) as client:
        api = PDFApi(client)
        # Use async methods
        response = await api.create_pdf(
            CreatePdfRequest(template_id='...', data={...})
        )

asyncio.run(generate_pdfs())
```

## Documentation

- [API Documentation](https://pdftemplateapi.com/docs)
- [Swagger UI](https://api.pdftemplateapi.com/docs)
- [Dashboard](https://pdftemplateapi.com/dashboard)

## Support

- Email: support@pdftemplateapi.com
- Issues: [GitHub Issues](https://github.com/TemplateFoxPDF/pythonsdk/issues)

## License

MIT License - see [LICENSE](LICENSE) for details.
