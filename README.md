# NexusView

NexusView is a lightweight Python package for rendering websites and YouTube videos directly inside Jupyter and IPython notebooks.

It helps notebook users preview external web pages and embedded videos without leaving their notebook environment.

[![PyPI version](https://img.shields.io/pypi/v/nexusview-package.svg)](https://pypi.org/project/nexusview-package/)
[![Python versions](https://img.shields.io/pypi/pyversions/nexusview-package.svg)](https://pypi.org/project/nexusview-package/)
[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](LICENSE)

---

## Features

- Render websites inside Jupyter notebooks using an IPython `IFrame`.
- Render YouTube videos using a privacy-friendly `youtube-nocookie.com` embed URL.
- Validate URLs before rendering.
- Raise a custom exception for invalid or unsupported URLs.
- Simple API for notebook-based workflows.

---

## Installation

Install from PyPI:

```bash
pip install nexusview-package
```

For local development:

```bash
git clone https://github.com/deep1305/NexusView.git
cd NexusView
pip install -e .
```

---

## Requirements

- Python 3.12+
- Jupyter Notebook, JupyterLab, Google Colab, or another IPython-compatible environment

---

## Quick Start

### Render a website

```python
from NexusView.site import render_site

render_site("https://www.python.org")
```

### Render a YouTube video

```python
from NexusView.youtube import render_youtube_video

render_youtube_video("https://www.youtube.com/watch?v=dQw4w9WgXcQ")
```

---

## API Overview

### `render_site(URL: str, width: str = "100%", height: str = "600") -> str`

Renders a web page inside the notebook using an IPython `IFrame`.

#### Parameters

- `URL`: Website URL to render.
- `width`: Width of the iframe. Default is `"100%"`.
- `height`: Height of the iframe. Default is `"600"`.

#### Returns

- `"success"` if the page is rendered successfully.

#### Raises

- `InvalidURLException` if the URL is invalid or unreachable.

#### Example

```python
from NexusView.site import render_site

status = render_site("https://pandas.pydata.org", width="100%", height="500")
print(status)
```

---

### `render_youtube_video(url: str, width: int = 780, height: int = 440)`

Renders a YouTube video inside the notebook.

#### Parameters

- `url`: YouTube video URL.
- `width`: Width of the embedded player.
- `height`: Height of the embedded player.

#### Returns

- `"success"` if the video is rendered successfully.

#### Raises

- `InvalidURLException` if the URL does not contain a valid YouTube video ID.

#### Example

```python
from NexusView.youtube import render_youtube_video

render_youtube_video("https://www.youtube.com/watch?v=ysz5S6PUM-U")
```

---

## Error Handling

NexusView provides a custom exception for invalid URLs:

```python
from NexusView.custom_exception import InvalidURLException
```

If an invalid or unsupported URL is provided, the package raises `InvalidURLException`.

---

## Supported Environments

NexusView is intended for use in:

- Jupyter Notebook
- JupyterLab
- Google Colab
- Other IPython-compatible notebook environments

It may not behave as expected in plain Python terminal scripts because rendering depends on IPython display utilities.

---

## Project Structure

```text
NexusView/
├── src/
│   └── NexusView/
│       ├── __init__.py
│       ├── custom_exception.py
│       ├── logger.py
│       ├── site.py
│       └── youtube.py
├── tests/
├── README.md
└── pyproject.toml
```

---

## Notes

- Website rendering depends on whether the target site allows iframe embedding.
- Some websites block iframe rendering through browser security headers such as `X-Frame-Options` or `Content-Security-Policy`.
- YouTube rendering extracts the video ID from the provided URL and embeds it using `youtube-nocookie.com`.

---

## Development

To install in editable mode:

```bash
pip install -e .
```

To run tests:

```bash
pytest
```

To run linting and type checks:

```bash
flake8 .
mypy src/
```

---

## Contributing

Contributions, bug reports, and feature requests are welcome.

1. Fork the repository.
2. Create a feature branch.
3. Make your changes.
4. Submit a pull request.

---

## License

This project is licensed under the Apache 2.0 License. See the [LICENSE](LICENSE) file for details.

---

## Links

- GitHub Repository: [deep1305/NexusView](https://github.com/deep1305/NexusView)
- PyPI: [nexusview-package](https://pypi.org/project/nexusview-package/)