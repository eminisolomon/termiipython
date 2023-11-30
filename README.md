# termiipython

[![Made in Nigeria](https://img.shields.io/badge/made%20in-nigeria-008751.svg?style=flat-square)](https://github.com/acekyd/made-in-nigeria)
[![Downloads](https://pepy.tech/badge/termiipython)](https://pepy.tech/project/termiipython)
[![Downloads](https://pepy.tech/badge/termiipython/month)](https://pepy.tech/project/termiipython)
[![Downloads](https://pepy.tech/badge/termiipython/week)](https://pepy.tech/project/termiipython)

Termii Python Library for Termii API

## Installation

```bash
pip install termiipython
```

## Usage

```python
from termiipython.token import Token
from termiipython.schemas.token import TokenType

token_client = Token()
token_client.authenticate_from_env()
response = token_client.send_token(
    message_type=TokenType.ALPHANUMERIC,
    receiver="2348152436475",
)
print(response)

```

```python
from termiipython.messaging import Messaging

messaging_client = Messaging()
messaging_client.authenticate_from_env()

receivers = ["2348152436475", "2347153436435"]
response = messaging_client.send_message(
    receivers=receivers,
    text="Hello all. Thanks for visiting."
)
print(response)
```

```python
from termiipython.campaign import Campaign

campaign_client = Campaign()
campaign_client.authenticate_from_env()
response = campaign_client.create_phonebook(
    name="Test", description="Test description."
)
print(response)
```

## Authentication.

There are two ways of authenticating requests:

1. With env variables:

To authenticate with environment variables set `TERMII_API_KEY`, `TERMII_ENDPOINT_URL`, `TERMII_SENDER_ID` to your termii api key, endpoint url and sender ID respectively. Then call client.authenticate_from_env()

Example:

```python
import os

from termiipython.campaign import Campaign

os.environ["TERMII_API_KEY"] = "ukwiwe4642eh"
os.environ["TERMII_ENDPOINT_URL"] = "https://api.ng.termii.com"
os.environ["TERMII_SENDER_ID"] = "Test"

campaign_client = Campaign()
campaign_client.authenticate_from_env()
```

2. A second method is to pass in the credentials directly. For that call `authenticate_direct()` on all clients and pass-in the credentials.

## Contributing

Interested in contributing? Check out the contributing guidelines. Please note that this project is released with a Code of Conduct. By contributing to this project, you agree to abide by its terms.

## License

`termiipython` was created by Solomon Olatunji. It is licensed under the terms of the MIT license.

Please send a private mail to `lordunyime@gmail.com` if you discover any security vulnerability. I'll be happy to work with you on a fix.
