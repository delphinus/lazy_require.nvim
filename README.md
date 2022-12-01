# What's this?

A tiny module to define function to load another module lazily.

# Usecase

A typical usecase for this plugin is for [packer.nvim][]. This can add a plugin to use with defining configuration processes.

[packer.nvim]: https://github.com/wbthomason/packer.nvim

```lua
use {
  "rcarriga/nvim-notify",
  config = function()
    require("notify").setup {
      render = "minimal",
      on_open = function(win)
        vim.api.nvim_win_set_config(win, { focusable = false })
      end,
    }
  end
}
```

With `lazy_require.nvim`, you can write the `setup` call directly on its `config` callback.

```lua
local lazy_require = require "lazy_require"

use {
  "rcarriga/nvim-notify",
  config = lazy_require("notify").setup {
    render = "minimal",
    on_open = function(win)
      vim.api.nvim_win_set_config(win, { focusable = false })
    end,
  },
}
```
