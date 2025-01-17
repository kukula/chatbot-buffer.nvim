# Chatbot-buffer.nvim

This is a plugin for interacting with the openai chat api. It's distinctive feature is that the conversation happens in a regular editable buffer so that it plays nicely with other vim plugins and so the user can revise the conversation history before continuing it.

Requires [plenary.nvim](https://github.com/nvim-lua/plenary.nvim), `curl`, and a [openai api token](https://platform.openai.com/account/api-keys) in the environment variable `OPENAI_API_TOKEN`.

## State of this plugin

This plugin is very work in progress, as in it only just works. There's no docs yet, read the source code (currently <300 lines in one file). Contributions and ideas welcome. Unless you really like exactly what I'm making here I'd recommend one of these two plugins instead:

- https://github.com/jackMort/ChatGPT.nvim
- https://github.com/dpayne/CodeGPT.nvim

### Planned features

- Handle error states better, currently if not online it just says loading forever, not sure what happens if openai's api is down or erroring
- Using virtual text for error and loading state (and maybe expose a function so it could be put in a status line)
- Use the streaming api so tokens can be added to the buffer immediately (1 token per ~100ms instead of the whole lot in 3-10 sec)
  - Is it possible to cancel a streaming response part way through, so we can shut it up when it's waffling? That would be sweet
- Add some formatting and/or concealing to the section markers
- Opt-in debug logging that saves all `curl` requests and responses to file

## Development

### Run tests

**Running tests requires [plenary.nvim](https://github.com/nvim-lua/plenary.nvim) to be checked out in the parent directory of _this_ repository.**

You can then run:

```bash
nvim --headless --noplugin -u tests/minimal.vim -c "PlenaryBustedDirectory tests/ {minimal_init = 'tests/minimal.vim'}"
```

Or if you want to run a single test file:

```bash
nvim --headless --noplugin -u tests/minimal.vim -c "PlenaryBustedDirectory tests/path_to_file.lua {minimal_init = 'tests/minimal.vim'}"
```
