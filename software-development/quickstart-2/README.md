# Quickstart

> (quickstart)=



libtmux allows for developers and system administrators to control live tmux
sessions using python code.

In this example, we will la

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
(quickstart)=

# Quickstart

libtmux allows for developers and system administrators to control live tmux
sessions using python code.

In this example, we will launch a tmux session and control the windows
from inside a live tmux session.

(requirements)=

## Requirements

- [tmux] 3.2a or newer
- [pip] - for this handbook's examples

[tmux]: https://tmux.github.io/

(installation)=

## Installation

Next, ensure `libtmux` is installed:

```console
$ pip install --user libtmux
```

(developmental-releases)=

### Developmental releases

New versions of libtmux are published to PyPI as alpha, beta, or release candidates. In their
versions you will see notification like `a1`, `b1`, and `rc1`, respectively. `1.10.0b4` would mean
the 4th beta release of `1.10.0` before general availability.

- [pip]\:

  ```console
  $ pip install --user --upgrade --pre libtmux
  ```

- [pipx]\:

  ```console
  $ pipx install \
      --suffix=@next \
      --pip-args '\--pre' \
      --force \
      'libtmux'
  ```

  Usage: `libtmux@next [command]`

- [uv tool install][uv-tools]\:

  ```console
  $ uv tool install --prerelease=allow libtmux
  ```

- [uv]\:

  ```console
  $ uv add libtmux --prerelease allow
  ```

- [uvx]\:

  ```console
  $ uvx --from 'libtmux' --prerelease allow python
  ```

via trunk (can break easily):

- [pip]\:

  ```console
  $ pip install --user -e git+https://github.com/tmux-python/libtmux.git#egg=libtmux
  ```

- [pipx]\:

  ```console
  $ pipx install \
      --suffix=@master \
      --force \
      'libtmux @ git+https://github.com/tmux-python/libtmux.git@master'
  ```

- [uv]\:

  ```console
  $ uv tool install libtmux --from git+https://github.com/tmux-python/libtmux.git
  ```

[pip]: https://pip.pypa.io/en/stable/
[pipx]: https://pypa.github.io/pipx/docs/
[uv]: https://docs.astral.sh/uv/
[uv-tools]: https://docs.astral.sh/uv/concepts/tools/
[uvx]: https://docs.astral.sh/uv/guides/tools/
[ptpython]: https://github.com/prompt-toolkit/ptpython

## Start a t

*[truncated — see source for full prompt]*