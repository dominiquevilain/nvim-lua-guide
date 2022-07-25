:arrow_upper_left: (Feeling lost? Use the GitHub TOC!)

# Neovim에서 Lua 사용 시작하기

## 번역

- [:cn: Chinese version](https://github.com/glepnir/nvim-lua-guide-zh)
- [:es: Spanish version](https://github.com/RicardoRien/nvim-lua-guide/blob/master/README.esp.md)
- [:brazil: Portuguese version](https://github.com/npxbr/nvim-lua-guide/blob/master/README.pt-br.md)
- [:jp: Japanese version](https://github.com/willelz/nvim-lua-guide-ja/blob/master/README.ja.md)
- [:ru: Russian version](https://github.com/kuator/nvim-lua-guide-ru)
- [🇺🇦 Ukrainian version](https://github.com/famiclone/nvim-lua-guide-ua)

## 소개

[네오빔에서 first-class 언어](https://github.com/neovim/neovim/wiki/FAQ#why-embed-lua-instead-of-x)로서 [통합된 루아](https://www.youtube.com/watch?v=IP3J56sKtn0)는 킬러 피쳐들 중 하나로 자리잡고 있습니다.
하지만 루아로 플러그인 작성하는 방법에 대해 배울 수 있는 자료는 빔스크립트로 작성하는 방법에 비해 많지 않습니다.
그래서 사람들이 좀 더 쉽게 시작할 수 있도록 기본적인 정보를 제공하려고 합니다.

이 가이드는 당신이 최소 Neovim 0.5 버전 이상을 사용하고 있다고 가정합니다.

### 루아 배우기

루아에 익숙하지 않다면 여기 시작하기에 좋은 자료들이 많이 있습니다.

- ['X를 Y분 만에 배우자'의 루아 페이지](https://learnxinyminutes.com/docs/lua/)에서는 기본적인 것들을 빠르게 훑어볼 수 있습니다.
- [이 가이드](https://github.com/medwatt/알림s/blob/main/Lua/Lua_Quick_Guide.ipynb)도 빠르게 시작하기 좋은 자료입니다.
- 당신이 비디오로 배우는 것을 더 선호한다면 Derek Banas의 [1 시간짜리 튜토리얼](https://www.youtube.com/watch?v=iMacxZQMPXs)도 있습니다.
- 실행 가능한 예제와 함께 좀 더 인터랙티브하게 배우고 싶다면 [루아 스크립트 튜토리얼](https://www.luascript.dev/learn)도 있습니다.
- [루아 유저 위키](http://lua-users.org/wiki/LuaDirectory)에는 루아와 관련된 유용한 정보들이 많이 있습니다.
- [루아 공식 레퍼런스 매뉴얼](https://www.lua.org/manual/5.1/)은 가장 광범위한 자료를 둘러볼 수 있습니다.(빔 에디터 내에서 읽고 싶다면 Vimdoc 플러그인으로도 있습니다.: [milisims/nvim-luaref](https://github.com/milisims/nvim-luaref))

It should also be noted that Lua is a very clean and simple language. It is easy to learn, especially if you have experience with similar scripting languages like JavaScript. You may already know more Lua than you realise!

루아는 정말 깔끔하고 단순한 언어라는 것을 먼저 말하고 시작하고 싶습니다.
자바스크립트같은 스트립팅 언어에 대한 경험이 있다면 정말 쉽게 배울 수 있습니다. 그렇지 않더라도요.
아마도 이미 생각보다 루아에 대해 더 많은 것을 알고 있을지도 몰라요.

알림: 네오빔에 내장된 루아 컴파일러는 [LuaJIT](https://staff.fnwi.uva.nl/h.vandermeer/docs/lua/luajit/luajit_intro.html) 2.1.0 버전입니다. 루아 5.1 버전과 호환 가능합니다.

### 네오빔에서 루아 작성하기에 대한 튜토리얼들

루아로 네오빔 설정하기에 관해 다음 튜토리얼들이 이미 있습니다. 그 중에서 이 가이드를 쓰는데 도움 받은 것도 있습니다. 작성자들에게 정말 감사합니다.

- [teukka.tech - From init.vim to init.lua](https://teukka.tech/luanvim.html)
- [dev.to - How to write neovim plugins in Lua](https://dev.to/2nit/how-to-write-neovim-plugins-in-lua-5cca)
- [dev.to - How to make UI for neovim plugins in Lua](https://dev.to/2nit/how-to-make-ui-for-neovim-plugins-in-lua-3b6e)
- [ms-jpq - Neovim Async Tutorial](https://github.com/ms-jpq/neovim-async-tutorial)
- [oroques.dev - Neovim 0.5 features and the switch to init.lua](https://oroques.dev/notes/neovim-init/)
- [Building A Vim Statusline from Scratch - jdhao's blog](https://jdhao.github.io/2019/11/03/vim_custom_statusline/)
- [Configuring Neovim using Lua](https://icyphox.sh/blog/nvim-lua/)
- [Devlog | Everything you need to know to configure neovim using lua](https://vonheikemen.github.io/devlog/tools/configuring-neovim-using-lua/)

### 도움 될만한 플러그인들

- [Vimpeccable](https://github.com/svermeulen/vimpeccable) - 루아로 .vimrc 작성할 때 도와주는 플러그인
- [plenary.nvim](https://github.com/nvim-lua/plenary.nvim) - 여러 번 작성하기 싫은 루아 함수들 (헬퍼 함수)
- [popup.nvim](https://github.com/nvim-lua/popup.nvim) - vim 팝업 API를 Neovim에서 구현한 것 
- [nvim_utils](https://github.com/norcalli/nvim_utils)
- [nvim-luadev](https://github.com/bfredl/nvim-luadev) - 루아 플러그인들을 위한 REPL/debug 콘솔
- [nvim-luapad](https://github.com/rafcamlet/nvim-luapad) - 내장된 루아 엔진과 실시간으로 상호작용 할 수 있는 네오빔 스크래치패드
- [nlua.nvim](https://github.com/tjdevries/nlua.nvim) - Neovim을 위한 루아 개발 도구
- [BetterLua.vim](https://github.com/euclidianAce/BetterLua.vim) - 더 나은 루아 구문(syntax) 하이라이팅

## Lua 파일들은 어디에 넣나요

### init.lua

Neovim은 `init.vim` 대신 `init.lua` 파일을 설정(configuration) 파일로 로딩할 수도 있습니다.

알림: `init.lua` is of course _completely_ optional. Support for `init.vim` is not going away and is still a valid option for configuration. Do keep in mind that some features are not 100% exposed to Lua yet.

알림: `init.lua` 파일을 사용하는 것은 물론 _완전히_ 선택 가능합니다. `init.vim`을 사용해도 상관 없으며 여전히 유효한 설정입니다. vim의 기능들 중 몇몇은 아직 루아로 접근할 수 없다는 것도 기억하면 좋습니다.

자세한 정보:
- [`:help config`](https://neovim.io/doc/user/starting.html#config)

### 모듈

루아 모듈들은 Neovim의 `runtimepath` (대부분의 \*nix 시스템 [*맥 | 리눅스*] 에서는 `~/.config/nvim/lua`, 윈도우에서는 `~/AppData/Local/nvim/lua` ) 안의 `lua/` 폴더 안에 위치합니다. 이 폴더 안에 있는 루아 파일들은 모듈로서 `require()` 할 수 있습니다.

다음 폴더 구조를 예시로 한 번 봐봅시다:

```text
📂 ~/.config/nvim
├── 📁 after
├── 📁 ftplugin
├── 📂 lua
│  ├── 🌑 myluamodule.lua
│  └── 📂 other_modules
│     ├── 🌑 anothermodule.lua
│     └── 🌑 init.lua
├── 📁 pack
├── 📁 plugin
├── 📁 syntax
└── 🇻 init.vim
```

다음 루아 코드는 `myloamodule.lua` 파일을 불러옵니다:

```lua
require('myluamodule')
```

`.lua` 확장자가 없는 것을 볼 수 있습니다.

비슷하게, `other_modules/anothermodule.lua` 파일을 불러오는 것도 다음과 같습니다:

```lua
require('other_modules.anothermodule')
-- or
require('other_modules/anothermodule')
```

경로 구분자는 `.`이나 `/`로 표기됩니다.

`init.lua` 파일을 포함하고 있는 폴더는 파일 이름을 지정하지 않아도 바로 불러올 수 있습니다.

```lua
require('other_modules') -- loads other_modules/init.lua
```

존재하지 않는 모듈이나 구문 에러를 포함하고 있는 모듈을 불러오게 되면 현재 실행 중인 스크립트가 종료됩니다.
`pcall()` 함수를 사용하면 에러로 인해 스크립트가 종료되는 것을 방지할 수 있습니다.

```lua
local ok, _ = pcall(require, 'module_with_error')
if not ok then
  -- not loaded
end
```

자세한 정보:
- [`:help lua-require`](https://neovim.io/doc/user/lua.html#lua-require)

#### Tips

루아 플러그인들 중 몇몇은 그 플러그인의 `lua/` 폴더 안에 동일한 파일 이름이 존재할 수도 있습니다. 그럴 경우 이름공간([namespace](https://ko.wikipedia.org/wiki/%EC%9D%B4%EB%A6%84%EA%B3%B5%EA%B0%84)) 충돌로 이어질 수 있습니다.

만약 두개의 다른 플러그인이 `lua/main.lua` 파일을 가지고 있다면, `require('main')` 을 실행할 때 어떤 파일을 불러야 하는지 알기 힘듭니다.

그래서 당신의 설정 파일이나 플러그인들의 namespace를 최상위 폴더와 같이 관리하는 것도 좋은 아이디어일 수 있습니다. 다음과 같이요:
`lua/plugin_name/main.lua`


### Runtime files

Vimscript 파일들과 마찬가지로, 루아 파일들도 당신의 `runtimepath`에 지정된 특별한 폴더들에서 자동적으로 불러와질 수 있습니다. 현재는 다음 폴더들이 지원되고 있습니다:

- `colors/`
- `compiler/`
- `ftplugin/`
- `ftdetect/`
- `indent/`
- `plugin/`
- `syntax/`

알림: runtime 디렉터리에서는 모든 `*.vim*` 파일들이 `*.lua` 파일들보다 먼저 불러와집니다.

자세한 정보:
- [`:help 'runtimepath'`](https://neovim.io/doc/user/options.html#'runtimepath')
- [`:help load-plugins`](https://neovim.io/doc/user/starting.html#load-plugins)

#### Tips

runtime 파일들이 Lua 모듈 시스템을 기반으로 하지 않기 때문에 두 플러그인들이 문제 없이 `plugin/main.lua` 파일을 가지고 있을 수 있습니다.

## Vimscript에서 Lua 사용하기

### :lua

이 명령어는 루아 코드 조각을 실행합니다.

```vim
:lua require('myluamodule')
```

여러 줄의 스크립트는 [heredoc](https://ko.wikipedia.org/wiki/%ED%9E%88%EC%96%B4_%EB%8F%84%ED%81%90%EB%A8%BC%ED%8A%B8)구문을 사용해 실행할 수 있습니다:

```vim
echo "Here's a bigger chunk of Lua code"

lua << EOF
local mod = require('mymodule')
local tbl = {1, 2, 3}

for k, v in ipairs(tbl) do
    mod.method(v)
end

print(tbl)
EOF
```

알림: `:lua` 명령어는 각각의 scope를 가지고 있으며 `local` 키워드로 선언된 변수들은 명령어 밖에서 접근할 수 없습니다. 다음은 작동하지 않습니다:

```vim
:lua local foo = 1
:lua print(foo)
" prints 'nil' instead of '1'
```

알림 2: 루아의 `print()` 함수는 `:echomsg` 명령어와 비슷하게 작동합니다. 실행 결과가 message-history에 저장되며 이는 `:silent` 커맨드를 사용해 보이지 않게 할수도 있습니다.

자세한 정보:

- [`:help :lua`](https://neovim.io/doc/user/lua.html#Lua)
- [`:help :lua-heredoc`](https://neovim.io/doc/user/lua.html#:lua-heredoc)

### :luado

이 명령어는 현재 버퍼에 라인들의 특정한 범위에 루아 코드를 실행합니다. 만약 범위가 지정되지 않았다면 버퍼 전체에서 실행됩니다. 어떤 string이든 루아 코드에서 `return`되면, 어떤 라인들이 바뀌어야 할지 정해집니다.

다음 명령은 현재 버퍼의 모든 라인을 `hello world`로 변경합니다:

```vim
:luado return 'hello world'
```

`line`과 `linenr` 변수도 제공됩니다. 각 라인들을 하나씩 반복하는 중에 `linenr`의 숫자는 라인의 인덱스, 그 라인의 내용이 `line` 입니다. 다음 명령어는 2로 나눠질 수 있는 라인들을 대문자로 변경합니다.

```vim
:luado if linenr % 2 == 0 then return line:upper() end
```

자세한 정보:

- [`:help :luado`](https://neovim.io/doc/user/lua.html#:luado)

### 루아 파일 가져오기 (Sourcing Lua files)

Neovim은 루아 파일을 가져오기 위해 다음 3개의 실행 명령어들을 제공합니다.

- `:luafile`
- `:source`
- `:runtime`

`:luafile`과 `:source`는 비슷합니다:

```vim
:luafile ~/foo/bar/baz/myluafile.lua
:luafile %
:source ~/foo/bar/baz/myluafile.lua
:source %
```

`:source`는 범위도 지정할 수 있습니다. 스크립트 파일의 일부분만 실행하고 싶을 때 유용합니다:

```vim
:1,10source
```

`:runtime`은 조금 다릅니다: `runtimepath` 옵션을 사용해서 어떤 파일을 가져올지 정할 수 있습니다. 더 많은 정보는 [`:help :runtime`](https://neovim.io/doc/user/repeat.html#:runtime)에서 확인할 수 있습니다.

자세한 정보:

- [`:help :luafile`](https://neovim.io/doc/user/lua.html#:luafile)
- [`:help :source`](https://neovim.io/doc/user/repeat.html#:source)
- [`:help :runtime`](https://neovim.io/doc/user/repeat.html#:runtime)

#### 루아 파일 가져오기 (sourcing) vs require() 호출하기:

`require()` 함수를 호출하는 것과 직접 루아 파일을 소싱하는 것의 차이와 어떤 것을 언제 사용해야 할지 궁금할 겁니다. 둘은 다음과 같은 서로 다른 사용 사례들이 있습니다:

- `require()`:
    - is a built-in Lua function. It allows you to take advantage of Lua's module system
    - 루아의 기본 빌트인 함수입니다. 
    - searches for modules in `lua/` folders in your `'runtimepath'`
    - keeps track of what modules have been loaded and prevents a script from being parsed and executed a second time. If you change the file containing the code for a module and try to `require()` it a second time while Neovim is running, the module will not actually update
- `:luafile`, `:source` and `:runtime`:
    - are Ex commands. They do not support modules
    - execute the contents of a script regardless of whether it has been executed before
    - `:luafile` and `:source` take a path that is either absolute or relative to the working directory of the current window
    - `:runtime` uses the `'runtimepath'` option to find files

Files sourced via `:source`, `:runtime` or automatically from runtime directories will also show up in `:scriptnames` and `--startuptime`

### luaeval()

This built-in Vimscript function evaluates a Lua expression string and returns its value. Lua data types are automatically converted to Vimscript types (and vice versa).

```vim
" You can store the result in a variable
let variable = luaeval('1 + 1')
echo variable
" 2
let concat = luaeval('"Lua".." is ".."awesome"')
echo concat
" 'Lua is awesome'

" List-like tables are converted to Vim lists
let list = luaeval('{1, 2, 3, 4}')
echo list[0]
" 1
echo list[1]
" 2
" 알림 that unlike Lua tables, Vim lists are 0-indexed

" Dict-like tables are converted to Vim dictionaries
let dict = luaeval('{foo = "bar", baz = "qux"}')
echo dict.foo
" 'bar'

" Same thing for booleans and nil
echo luaeval('true')
" v:true
echo luaeval('nil')
" v:null

" You can create Vimscript aliases for Lua functions
let LuaMathPow = luaeval('math.pow')
echo LuaMathPow(2, 2)
" 4
let LuaModuleFunction = luaeval('require("mymodule").myfunction')
call LuaModuleFunction()

" It is also possible to pass Lua functions as values to Vim functions
lua X = function(k, v) return string.format("%s:%s", k, v) end
echo map([1, 2, 3], luaeval("X"))
```

`luaeval()` takes an optional second argument that allows you to pass data to the expression. You can then access that data from Lua using the magic global `_A`:

```vim
echo luaeval('_A[1] + _A[2]', [1, 1])
" 2

echo luaeval('string.format("Lua is %s", _A)', 'awesome')
" 'Lua is awesome'
```

자세한 정보:
- [`:help luaeval()`](https://neovim.io/doc/user/lua.html#luaeval())

### v:lua

This global Vim variable allows you to call Lua functions in the global namespace ([`_G`](https://www.lua.org/manual/5.1/manual.html#pdf-_G)) directly from Vimscript. Again, Vim data types are converted to Lua types and vice versa.

```vim
call v:lua.print('Hello from Lua!')
" 'Hello from Lua!'

let scream = v:lua.string.rep('A', 10)
echo scream
" 'AAAAAAAAAA'

" How about a nice statusline?
lua << EOF
function _G.statusline()
    local filepath = '%f'
    local align_section = '%='
    local percentage_through_file = '%p%%'
    return string.format(
        '%s%s%s',
        filepath,
        align_section,
        percentage_through_file
    )
end
EOF

set statusline=%!v:lua.statusline()

" Also works in expression mappings
lua << EOF
function _G.check_back_space()
    local col = vim.api.nvim_win_get_cursor(0)[2]
    return (col == 0 or vim.api.nvim_get_current_line():sub(col, col):match('%s')) and true
end
EOF

inoremap <silent> <expr> <Tab>
    \ pumvisible() ? "\<C-N>" :
    \ v:lua.check_back_space() ? "\<Tab>" :
    \ completion#trigger_completion()

" Call a function from a Lua module by using single quotes and omitting parentheses:
call v:lua.require'module'.foo()
```

자세한 정보:
- [`:help v:lua`](https://neovim.io/doc/user/eval.html#v:lua)
- [`:help v:lua-call`](https://neovim.io/doc/user/lua.html#v:lua-call)

#### Caveats

This variable can only be used to call functions. The following will always throw an error:

```vim
" Aliasing functions doesn't work
let LuaPrint = v:lua.print

" Accessing dictionaries doesn't work
echo v:lua.some_global_dict['key']

" Using a function as a value doesn't work
echo map([1, 2, 3], v:lua.global_callback)
```

### Tips

You can get Lua syntax highlighting inside .vim files by putting `let g:vimsyn_embed = 'l'` in your configuration file. See [`:help g:vimsyn_embed`](https://neovim.io/doc/user/syntax.html#g:vimsyn_embed) for more on this option.

## The vim namespace

Neovim exposes a global `vim` variable which serves as an entry point to interact with its APIs from Lua. It provides users with an extended "standard library" of functions as well as various sub-modules.

Some notable functions and modules include:

- `vim.inspect`: transform Lua objects into human-readable strings (useful for inspecting tables)
- `vim.regex`: use Vim regexes from Lua
- `vim.api`: module that exposes API functions (the same API used by remote plugins)
- `vim.ui`: overridable UI functions that can be leveraged by plugins
- `vim.loop`: module that exposes the functionality of Neovim's event-loop (using LibUV)
- `vim.lsp`: module that controls the built-in LSP client
- `vim.treesitter`: module that exposes the functionality of the tree-sitter library

This list is by no means comprehensive. If you wish to know more about what's made available by the `vim` variable, [`:help lua-stdlib`](https://neovim.io/doc/user/lua.html#lua-stdlib) and [`:help lua-vim`](https://neovim.io/doc/user/lua.html#lua-vim) are the way to go. Alternatively, you can do `:lua print(vim.inspect(vim))` to get a list of every module. API functions are documented under [`:help api-global`](https://neovim.io/doc/user/api.html#api-global).

#### Tips

Writing `print(vim.inspect(x))` every time you want to inspect the contents of an object can get pretty tedious. It might be worthwhile to have a global wrapper function somewhere in your configuration (in Neovim 0.7.0+, this function is built-in, see [`:help vim.pretty_print()`](https://neovim.io/doc/user/lua.html#vim.pretty_print())):

```lua
function _G.put(...)
  local objects = {}
  for i = 1, select('#', ...) do
    local v = select(i, ...)
    table.insert(objects, vim.inspect(v))
  end

  print(table.concat(objects, '\n'))
  return ...
end
```

You can then inspect the contents of an object very quickly in your code or from the command-line:

```lua
put({1, 2, 3})
```

```vim
:lua put(vim.loop)
```

Alternatively, you can use the `:lua` command to pretty-print a Lua expression by prefixing it with `=` (Neovim 0.7+ only):
```vim
:lua =vim.loop
```

Additionally, you may find that built-in Lua functions are sometimes lacking compared to what you would find in other languages (for example `os.clock()` only returns a value in seconds, not milliseconds). Be sure to look at the Neovim stdlib (and `vim.fn`, more on that later), it probably has what you're looking for.

## Using Vimscript from Lua

### vim.api.nvim_eval()

This function evaluates a Vimscript expression string and returns its value. Vimscript data types are automatically converted to Lua types (and vice versa).

It is the Lua equivalent of the `luaeval()` function in Vimscript

```lua
-- Data types are converted correctly
print(vim.api.nvim_eval('1 + 1')) -- 2
print(vim.inspect(vim.api.nvim_eval('[1, 2, 3]'))) -- { 1, 2, 3 }
print(vim.inspect(vim.api.nvim_eval('{"foo": "bar", "baz": "qux"}'))) -- { baz = "qux", foo = "bar" }
print(vim.api.nvim_eval('v:true')) -- true
print(vim.api.nvim_eval('v:null')) -- nil
```

#### Caveats

Unlike `luaeval()`, `vim.api.nvim_eval()` does not provide an implicit `_A` variable to pass data to the expression.

### vim.api.nvim_exec()

This function evaluates a chunk of Vimscript code. It takes in a string containing the source code to execute and a boolean to determine whether the output of the code should be returned by the function (you can then store the output in a variable, for example).

```lua
local result = vim.api.nvim_exec(
[[
let s:mytext = 'hello world'

function! s:MyFunction(text)
    echo a:text
endfunction

call s:MyFunction(s:mytext)
]],
true)

print(result) -- 'hello world'
```

#### Caveats

`nvim_exec` does not support script-local variables (`s:`) prior to Neovim 0.6.0

### vim.api.nvim_command()

This function executes an ex command. It takes in a string containing the command to execute.

```lua
vim.api.nvim_command('new')
vim.api.nvim_command('wincmd H')
vim.api.nvim_command('set nonumber')
vim.api.nvim_command('%s/foo/bar/g')
```

### vim.cmd()

Alias for `vim.api.nvim_exec()`. Only the command argument is needed, `output` is always set to `false`.

```lua
vim.cmd('buffers')
vim.cmd([[
let g:multiline_list = [
            \ 1,
            \ 2,
            \ 3,
            \ ]

echo g:multiline_list
]])
```

#### Tips

Since you have to pass strings to these functions, you often end up having to escape backslashes:

```lua
vim.cmd('%s/\\Vfoo/bar/g')
```

Double bracketed strings are easier to use as they do not require escaping characters:

```lua
vim.cmd([[%s/\Vfoo/bar/g]])
```

### vim.api.nvim_replace_termcodes()

This API function allows you to escape terminal codes and Vim keycodes.

You may have come across mappings like this one:

```vim
inoremap <expr> <Tab> pumvisible() ? "\<C-N>" : "\<Tab>"
```

Trying to do the same in Lua can prove to be a challenge. You might be tempted to do it like this:

```lua
function _G.smart_tab()
    return vim.fn.pumvisible() == 1 and [[\<C-N>]] or [[\<Tab>]]
end

vim.api.nvim_set_keymap('i', '<Tab>', 'v:lua.smart_tab()', {expr = true, noremap = true})
```

only to find out that the mapping inserts `\<Tab>` and `\<C-N>` literally...

Being able to escape keycodes is actually a Vimscript feature. Aside from the usual escape sequences like `\r`, `\42` or `\x10` that are common to many programming languages, Vimscript `expr-quotes` (strings surrounded with double quotes) allow you to escape the human-readable representation of Vim keycodes.

Lua doesn't have such a feature built-in. Fortunately, Neovim has an API function for escaping terminal codes and keycodes: `nvim_replace_termcodes()`

```lua
print(vim.api.nvim_replace_termcodes('<Tab>', true, true, true))
```

This is a little verbose. Making a reusable wrapper can help:

```lua
-- The function is called `t` for `termcodes`.
-- You don't have to call it that, but I find the terseness convenient
local function t(str)
    -- Adjust boolean arguments as needed
    return vim.api.nvim_replace_termcodes(str, true, true, true)
end

print(t'<Tab>')
```

Coming back to our earlier example, this should now work as expected:

```lua
local function t(str)
    return vim.api.nvim_replace_termcodes(str, true, true, true)
end

function _G.smart_tab()
    return vim.fn.pumvisible() == 1 and t'<C-N>' or t'<Tab>'
end

vim.api.nvim_set_keymap('i', '<Tab>', 'v:lua.smart_tab()', {expr = true, noremap = true})
```

This is not necessary with `vim.keymap.set()` as it automatically transforms vim keycodes returned by Lua functions in `expr` mappings by default:

```lua
vim.keymap.set('i', '<Tab>', function()
    return vim.fn.pumvisible() == 1 and '<C-N>' or '<Tab>'
end, {expr = true})
```

자세한 정보:

- [`:help keycodes`](https://neovim.io/doc/user/intro.html#keycodes)
- [`:help expr-quote`](https://neovim.io/doc/user/eval.html#expr-quote)
- [`:help nvim_replace_termcodes()`](https://neovim.io/doc/user/api.html#nvim_replace_termcodes())

## Managing vim options

### Using api functions

Neovim provides a set of API functions to either set an option or get its current value:

- Global options:
    - [`vim.api.nvim_set_option()`](https://neovim.io/doc/user/api.html#nvim_set_option())
    - [`vim.api.nvim_get_option()`](https://neovim.io/doc/user/api.html#nvim_get_option())
- Buffer-local options:
    - [`vim.api.nvim_buf_set_option()`](https://neovim.io/doc/user/api.html#nvim_buf_set_option())
    - [`vim.api.nvim_buf_get_option()`](https://neovim.io/doc/user/api.html#nvim_buf_get_option())
- Window-local options:
    - [`vim.api.nvim_win_set_option()`](https://neovim.io/doc/user/api.html#nvim_win_set_option())
    - [`vim.api.nvim_win_get_option()`](https://neovim.io/doc/user/api.html#nvim_win_get_option())

They take a string containing the name of the option to set/get as well as the value you want to set it to.

Boolean options (like `(no)number`) have to be set to either `true` or `false`:

```lua
vim.api.nvim_set_option('smarttab', false)
print(vim.api.nvim_get_option('smarttab')) -- false
```

Unsurprisingly, string options have to be set to a string:

```lua
vim.api.nvim_set_option('selection', 'exclusive')
print(vim.api.nvim_get_option('selection')) -- 'exclusive'
```

Number options accept a number:

```lua
vim.api.nvim_set_option('updatetime', 3000)
print(vim.api.nvim_get_option('updatetime')) -- 3000
```

Buffer-local and window-local options also need a buffer number or a window number (using `0` will set/get the option for the current buffer/window):

```lua
vim.api.nvim_win_set_option(0, 'number', true)
vim.api.nvim_buf_set_option(10, 'shiftwidth', 4)
print(vim.api.nvim_win_get_option(0, 'number')) -- true
print(vim.api.nvim_buf_get_option(10, 'shiftwidth')) -- 4
```

### Using meta-accessors

A few meta-accessors are available if you want to set options in a more "idiomatic" way. They essentially wrap the above API functions and allow you to manipulate options as if they were variables:

- [`vim.o`](https://neovim.io/doc/user/lua.html#vim.o): behaves like `:let &{option-name}`
- [`vim.go`](https://neovim.io/doc/user/lua.html#vim.go): behaves like `:let &g:{option-name}`
- [`vim.bo`](https://neovim.io/doc/user/lua.html#vim.bo): behaves like `:let &l:{option-name}` for buffer-local options
- [`vim.wo`](https://neovim.io/doc/user/lua.html#vim.wo): behaves like `:let &l:{option-name}` for window-local options

```lua
vim.o.smarttab = false -- let &smarttab = v:false
print(vim.o.smarttab) -- false
vim.o.isfname = vim.o.isfname .. ',@-@' -- on Linux: let &isfname = &isfname .. ',@-@'
print(vim.o.isfname) -- '@,48-57,/,.,-,_,+,,,#,$,%,~,=,@-@'

vim.bo.shiftwidth = 4
print(vim.bo.shiftwidth) -- 4
```

You can specify a number for buffer-local and window-local options. If no number is given, the current buffer/window is used:

```lua
vim.bo[4].expandtab = true -- same as vim.api.nvim_buf_set_option(4, 'expandtab', true)
vim.wo.number = true -- same as vim.api.nvim_win_set_option(0, 'number', true)
```

These wrappers also have more sophisticated `vim.opt*` variants that provide convenient mechanisms for setting options in Lua. They're similar to what you might be used to in your `init.vim`:

- `vim.opt`: behaves like `:set`
- `vim.opt_global`: behaves like `:setglobal`
- `vim.opt_local`: behaves like `:setlocal`

```lua
vim.opt.smarttab = false
print(vim.opt.smarttab:get()) -- false
```

Some options can be set using Lua tables:

```lua
vim.opt.completeopt = {'menuone', 'noselect'}
print(vim.inspect(vim.opt.completeopt:get())) -- { "menuone", "noselect" }
```

Wrappers for list-like, map-like and set-like options also come with methods and metamethods that work similarly to their `:set+=`, `:set^=` and `:set-=` counterparts in Vimscript.

```lua
vim.opt.shortmess:append({ I = true })
-- alternative form:
vim.opt.shortmess = vim.opt.shortmess + { I = true }

vim.opt.whichwrap:remove({ 'b', 's' })
-- alternative form:
vim.opt.whichwrap = vim.opt.whichwrap - { 'b', 's' }
```

Be sure to look at [`:help vim.opt`](https://neovim.io/doc/user/lua.html#vim.opt) for more information.

자세한 정보:
- [`:help lua-vim-options`](https://neovim.io/doc/user/lua.html#lua-vim-options)

## Managing vim internal variables

### Using api functions

Much like options, internal variables have their own set of API functions:

- Global variables (`g:`):
    - [`vim.api.nvim_set_var()`](https://neovim.io/doc/user/api.html#nvim_set_var())
    - [`vim.api.nvim_get_var()`](https://neovim.io/doc/user/api.html#nvim_get_var())
    - [`vim.api.nvim_del_var()`](https://neovim.io/doc/user/api.html#nvim_del_var())
- Buffer variables (`b:`):
    - [`vim.api.nvim_buf_set_var()`](https://neovim.io/doc/user/api.html#nvim_buf_set_var())
    - [`vim.api.nvim_buf_get_var()`](https://neovim.io/doc/user/api.html#nvim_buf_get_var())
    - [`vim.api.nvim_buf_del_var()`](https://neovim.io/doc/user/api.html#nvim_buf_del_var())
- Window variables (`w:`):
    - [`vim.api.nvim_win_set_var()`](https://neovim.io/doc/user/api.html#nvim_win_set_var())
    - [`vim.api.nvim_win_get_var()`](https://neovim.io/doc/user/api.html#nvim_win_get_var())
    - [`vim.api.nvim_win_del_var()`](https://neovim.io/doc/user/api.html#nvim_win_del_var())
- Tabpage variables (`t:`):
    - [`vim.api.nvim_tabpage_set_var()`](https://neovim.io/doc/user/api.html#nvim_tabpage_set_var())
    - [`vim.api.nvim_tabpage_get_var()`](https://neovim.io/doc/user/api.html#nvim_tabpage_get_var())
    - [`vim.api.nvim_tabpage_del_var()`](https://neovim.io/doc/user/api.html#nvim_tabpage_del_var())
- Predefined Vim variables (`v:`):
    - [`vim.api.nvim_set_vvar()`](https://neovim.io/doc/user/api.html#nvim_set_vvar())
    - [`vim.api.nvim_get_vvar()`](https://neovim.io/doc/user/api.html#nvim_get_vvar())

With the exception of predefined Vim variables, they can also be deleted (the `:unlet` command is the equivalent in Vimscript). Local variables (`l:`), script variables (`s:`) and function arguments (`a:`) cannot be manipulated as they only make sense in the context of a Vim script, Lua has its own scoping rules.

If you are unfamiliar with what these variables do, [`:help internal-variables`](https://neovim.io/doc/user/eval.html#internal-variables) describes them in detail.

These functions take a string containing the name of the variable to set/get/delete as well as the value you want to set it to.

```lua
vim.api.nvim_set_var('some_global_variable', { key1 = 'value', key2 = 300 })
print(vim.inspect(vim.api.nvim_get_var('some_global_variable'))) -- { key1 = "value", key2 = 300 }
vim.api.nvim_del_var('some_global_variable')
```

Variables that are scoped to a buffer, a window or a tabpage also receive a number (using `0` will set/get/delete the variable for the current buffer/window/tabpage):

```lua
vim.api.nvim_win_set_var(0, 'some_window_variable', 2500)
vim.api.nvim_tab_set_var(3, 'some_tabpage_variable', 'hello world')
print(vim.api.nvim_win_get_var(0, 'some_window_variable')) -- 2500
print(vim.api.nvim_buf_get_var(3, 'some_tabpage_variable')) -- 'hello world'
vim.api.nvim_win_del_var(0, 'some_window_variable')
vim.api.nvim_buf_del_var(3, 'some_tabpage_variable')
```

### Using meta-accessors

Internal variables can be manipulated more intuitively using these meta-accessors:

- [`vim.g`](https://neovim.io/doc/user/lua.html#vim.g): global variables
- [`vim.b`](https://neovim.io/doc/user/lua.html#vim.b): buffer variables
- [`vim.w`](https://neovim.io/doc/user/lua.html#vim.w): window variables
- [`vim.t`](https://neovim.io/doc/user/lua.html#vim.t): tabpage variables
- [`vim.v`](https://neovim.io/doc/user/lua.html#vim.v): predefined Vim variables
- [`vim.env`](https://neovim.io/doc/user/lua.html#vim.env): environment variables

```lua
vim.g.some_global_variable = {
    key1 = 'value',
    key2 = 300
}

print(vim.inspect(vim.g.some_global_variable)) -- { key1 = "value", key2 = 300 }

-- target a specific buffer/window/tabpage (Neovim 0.6+)
vim.b[2].myvar = 1
```

Some variable names may contain characters that cannot be used for identifiers in Lua. You can still manipulate these variables by using this syntax: `vim.g['my#variable']`.

To delete one of these variables, simply assign `nil` to it:

```lua
vim.g.some_global_variable = nil
```

자세한 정보:
- [`:help lua-vim-variables`](https://neovim.io/doc/user/lua.html#lua-vim-variables)

#### Caveats

You cannot add/update/delete keys from a dictionary stored in one of these variables. For example, this snippet of Vimscript code does not work as expected:

```vim
let g:variable = {}
lua vim.g.variable.key = 'a'
echo g:variable
" {}
```

You can use a temporary variable as a workaround:

```vim
let g:variable = {}
lua << EOF
local tmp = vim.g.variable
tmp.key = 'a'
vim.g.variable = tmp
EOF
echo g:variable
" {'key': 'a'}
```

This is a known issue:

- [Issue #12544](https://github.com/neovim/neovim/issues/12544)

## Calling Vimscript functions

### vim.fn.{function}()

`vim.fn` can be used to call a Vimscript function. Data types are converted back and forth from Lua to Vimscript.

```lua
print(vim.fn.printf('Hello from %s', 'Lua'))

local reversed_list = vim.fn.reverse({ 'a', 'b', 'c' })
print(vim.inspect(reversed_list)) -- { "c", "b", "a" }

local function print_stdout(chan_id, data, name)
    print(data[1])
end

vim.fn.jobstart('ls', { on_stdout = print_stdout })
```

Hashes (`#`) are not valid characters for identifiers in Lua, so autoload functions have to be called with this syntax:

```lua
vim.fn['my#autoload#function']()
```

The functionality of `vim.fn` is identical to `vim.call`, but allows a more Lua-like syntax.

It is distinct from `vim.api.nvim_call_function` in that converting Vim/Lua objects is automatic: `vim.api.nvim_call_function` returns a table for floating point numbers and does not accept Lua closures while `vim.fn` handles these types transparently.

자세한 정보:
- [`:help vim.fn`](https://neovim.io/doc/user/lua.html#vim.fn)

#### Tips

Neovim has an extensive library of powerful built-in functions that are very useful for plugins. See [`:help vim-function`](https://neovim.io/doc/user/eval.html#vim-function) for an alphabetical list and [`:help function-list`](https://neovim.io/doc/user/usr_41.html#function-list) for a list of functions grouped by topic.

Neovim API functions can be used directly through `vim.api.{..}`. See [`:help api`](https://neovim.io/doc/user/api.html#API) for information.

#### Caveats

Some Vim functions that should return a boolean return `1` or `0` instead. This isn't a problem in Vimscript as `1` is truthy and `0` falsy, enabling constructs like these:

```vim
if has('nvim')
    " do something...
endif
```

In Lua however, only `false` and `nil` are considered falsy, numbers always evaluate to `true` no matter their value. You have to explicitly check for `1` or `0`:

```lua
if vim.fn.has('nvim') == 1 then
    -- do something...
end
```

## Defining mappings

### API functions

Neovim provides a list of API functions to set, get and delete mappings:

- Global mappings:
    - [`vim.api.nvim_set_keymap()`](https://neovim.io/doc/user/api.html#nvim_set_keymap())
    - [`vim.api.nvim_get_keymap()`](https://neovim.io/doc/user/api.html#nvim_get_keymap())
    - [`vim.api.nvim_del_keymap()`](https://neovim.io/doc/user/api.html#nvim_del_keymap())
- Buffer-local mappings:
    - [`vim.api.nvim_buf_set_keymap()`](https://neovim.io/doc/user/api.html#nvim_buf_set_keymap())
    - [`vim.api.nvim_buf_get_keymap()`](https://neovim.io/doc/user/api.html#nvim_buf_get_keymap())
    - [`vim.api.nvim_buf_del_keymap()`](https://neovim.io/doc/user/api.html#nvim_buf_del_keymap())

Let's start with `vim.api.nvim_set_keymap()` and `vim.api.nvim_buf_set_keymap()`

The first argument passed to the function is a string containing the name of the mode for which the mapping will take effect:

| String value           | Help page     | Affected modes                           | Vimscript equivalent |
| ---------------------- | ------------- | ---------------------------------------- | -------------------- |
| `''` (an empty string) | `mapmode-nvo` | Normal, Visual, Select, Operator-pending | `:map`               |
| `'n'`                  | `mapmode-n`   | Normal                                   | `:nmap`              |
| `'v'`                  | `mapmode-v`   | Visual and Select                        | `:vmap`              |
| `'s'`                  | `mapmode-s`   | Select                                   | `:smap`              |
| `'x'`                  | `mapmode-x`   | Visual                                   | `:xmap`              |
| `'o'`                  | `mapmode-o`   | Operator-pending                         | `:omap`              |
| `'!'`                  | `mapmode-ic`  | Insert and Command-line                  | `:map!`              |
| `'i'`                  | `mapmode-i`   | Insert                                   | `:imap`              |
| `'l'`                  | `mapmode-l`   | Insert, Command-line, Lang-Arg           | `:lmap`              |
| `'c'`                  | `mapmode-c`   | Command-line                             | `:cmap`              |
| `'t'`                  | `mapmode-t`   | Terminal                                 | `:tmap`              |

The second argument is a string containing the left-hand side of the mapping (the key or set of keys that trigger the command defined in the mapping). An empty string is equivalent to `<Nop>`, which disables a key.

The third argument is a string containing the right-hand side of the mapping (the command to execute).

The final argument is a table containing boolean options for the mapping as defined in [`:help :map-arguments`](https://neovim.io/doc/user/map.html#:map-arguments) (including `noremap` and excluding `buffer`). Since Neovim 0.7.0, you can also pass a `callback` option to invoke a Lua function instead of the right-hand side when executing the mapping.

Buffer-local mappings also take a buffer number as their first argument (`0` sets the mapping for the current buffer).

```lua
vim.api.nvim_set_keymap('n', '<Leader><Space>', ':set hlsearch!<CR>', { noremap = true, silent = true })
-- :nnoremap <silent> <Leader><Space> :set hlsearch<CR>
vim.api.nvim_set_keymap('n', '<Leader>tegf',  [[<Cmd>lua require('telescope.builtin').git_files()<CR>]], { noremap = true, silent = true })
-- :nnoremap <silent> <Leader>tegf <Cmd>lua require('telescope.builtin').git_files()<CR>

vim.api.nvim_buf_set_keymap(0, '', 'cc', 'line(".") == 1 ? "cc" : "ggcc"', { noremap = true, expr = true })
-- :noremap <buffer> <expr> cc line('.') == 1 ? 'cc' : 'ggcc'

vim.api.nvim_set_keymap('n', '<Leader>ex', '', {
    noremap = true,
    callback = function()
        print('My example')
    end,
    -- Since Lua function don't have a useful string representation, you can use the "desc" option to document your mapping
    desc = 'Prints "My example" in the message area',
})
```

`vim.api.nvim_get_keymap()` takes a string containing the shortname of the mode for which you want the list of mappings (see table above). The return value is a table containing all global mappings for the mode.

```lua
print(vim.inspect(vim.api.nvim_get_keymap('n')))
-- :verbose nmap
```

`vim.api.nvim_buf_get_keymap()` takes an additional buffer number as its first argument (`0` will get mapppings for the current bufffer)

```lua
print(vim.inspect(vim.api.nvim_buf_get_keymap(0, 'i')))
-- :verbose imap <buffer>
```

`vim.api.nvim_del_keymap()` takes a mode and the left-hand side of a mapping.

```lua
vim.api.nvim_del_keymap('n', '<Leader><Space>')
-- :nunmap <Leader><Space>
```

Again, `vim.api.nvim_buf_del_keymap()`, takes a buffer number as its first argument, with `0` representing the current buffer.

```lua
vim.api.nvim_buf_del_keymap(0, 'i', '<Tab>')
-- :iunmap <buffer> <Tab>
```

### vim.keymap

:warning: The functions discussed in this section are only available in Neovim 0.7.0+

Neovim provides two functions to set/del mappings:
- [`vim.keymap.set()`](https://neovim.io/doc/user/lua.html#vim.keymap.set())
- [`vim.keymap.del()`](https://neovim.io/doc/user/lua.html#vim.keymap.del())

These are similar to the above API functions with added syntactic sugar.

`vim.keymap.set()` takes a string as its first argument. It can also be a table of strings to define mappings for multiple modes at once:

```lua
vim.keymap.set('n', '<Leader>ex1', '<Cmd>lua vim.notify("Example 1")<CR>')
vim.keymap.set({'n', 'c'}, '<Leader>ex2', '<Cmd>lua vim.notify("Example 2")<CR>')
```

The second argument is the left-hand side of the mapping.

The third argument is the right-hand side of the mapping, which can either be a string or a Lua function:

```lua
vim.keymap.set('n', '<Leader>ex1', '<Cmd>echomsg "Example 1"<CR>')
vim.keymap.set('n', '<Leader>ex2', function() print("Example 2") end)
vim.keymap.set('n', '<Leader>pl1', require('plugin').plugin_action)
-- To avoid the startup cost of requiring the module, you can wrap it in a function to require it lazily when invoking the mapping:
vim.keymap.set('n', '<Leader>pl2', function() require('plugin').plugin_action() end)
```

The fourth (optional) argument is a table of options that correspond to the options passed to `vim.api.nvim_set_keymap()`, with a few additions (see [`:help vim.keymap.set()`](https://neovim.io/doc/user/lua.html#vim.keymap.set()) for the full list).

```lua
vim.keymap.set('n', '<Leader>ex1', '<Cmd>echomsg "Example 1"<CR>', {buffer = true})
vim.keymap.set('n', '<Leader>ex2', function() print('Example 2') end, {desc = 'Prints "Example 2" to the message area'})
```

Defining keymaps with a Lua function is different from using a string. The usual way to show information about a keymap like `:nmap <Leader>ex1` will not output useful information (the string itself), but instead only show `Lua function`. It is recommended to add a `desc` key to describe the behavior of your keymap. This is especially important for documenting plugin mappings so users can understand the usage of the keymap more easily.

An interesting feature of this API is that it irons out some historical quirks of Vim mappings:
- Mappings are `noremap` by default, except when the `rhs` is a `<Plug>` mapping. This means you rarely have to think about whether a mapping should be recursive or not:
    ```lua
    vim.keymap.set('n', '<Leader>test1', '<Cmd>echo "test"<CR>')
    -- :nnoremap <Leader>test <Cmd>echo "test"<CR>

    -- If you DO want the mapping to be recursive, set the "remap" option to "true"
    vim.keymap.set('n', '>', ']', {remap = true})
    -- :nmap > ]

    -- <Plug> mappings don't work unless they're recursive, vim.keymap.set() handles that for you automatically
    vim.keymap.set('n', '<Leader>plug', '<Plug>(plugin)')
    -- :nmap <Leader>plug <Plug>(plugin)
    ```
- In `expr` mappings, `nvim_replace_termcodes()` is automatically applied to strings returned from Lua functions:
    ```lua
    vim.keymap.set('i', '<Tab>', function()
        return vim.fn.pumvisible == 1 and '<C-N>' or '<Tab>'
    end, {expr = true})
    ```

자세한 정보:
- [`:help recursive_mapping`](https://neovim.io/doc/user/map.html#recursive_mapping)

`vim.keymap.del()` works the same way but deletes mappings instead:

```lua
vim.keymap.del('n', '<Leader>ex1')
vim.keymap.del({'n', 'c'}, '<Leader>ex2', {buffer = true})
```

## Defining user commands

:warning: The API functions discussed in this section are only available in Neovim 0.7.0+

Neovim provides API functions for user-defined commands:

- Global user commands:
    - [`vim.api.nvim_create_user_command()`](https://neovim.io/doc/user/api.html#nvim_create_user_command())
    - [`vim.api.nvim_del_user_command()`](https://neovim.io/doc/user/api.html#nvim_del_user_command())
- Buffer-local user commands:
    - [`vim.api.nvim_buf_create_user_command()`](https://neovim.io/doc/user/api.html#nvim_buf_create_user_command())
    - [`vim.api.nvim_buf_del_user_command()`](https://neovim.io/doc/user/api.html#nvim_buf_del_user_command())

Let's start with `vim.api.nvim_create_user_command()`

The first argument passed to this function is the name of the command (which must start with an uppercase letter).

The second argument is the code to execute when invoking said command. It can either be:

A string (in which case it will be executed as Vimscript). You can use escape sequences like `<q-args>`, `<range>`, etc. like you would with `:command`
```lua
vim.api.nvim_create_user_command('Upper', 'echo toupper(<q-args>)', { nargs = 1 })
-- :command! -nargs=1 Upper echo toupper(<q-args>)

vim.cmd('Upper hello world') -- prints "HELLO WORLD"
```

Or a Lua function. It receives a dictionary-like table that contains the data normally provided by escape sequences (see [`:help nvim_create_user_command()`](https://neovim.io/doc/user/api.html#nvim_create_user_command()) for a list of available keys)
```lua
vim.api.nvim_create_user_command(
    'Upper',
    function(opts)
        print(string.upper(opts.args))
    end,
    { nargs = 1 }
)
```

The third argument lets you pass command attributes as a table (see [`:help command-attributes`](https://neovim.io/doc/user/map.html#command-attributes)). Since you can already define buffer-local user commands with `vim.api.nvim_buf_create_user_command()`, `-buffer` is not a valid attribute.

Two additional attributes are available:
- `desc` allows you to control what gets displayed when you run `:command {cmd}` on a command defined as a Lua callback. Similarly to keymaps, it is recommended to add a `desc` key to commands defined as Lua functions.
- `force` is equivalent to calling `:command!` and replaces a command if one with the same name already exists. It is true by default, unlike its Vimscript equivalent.

The `-complete` attribute can take a Lua function in addition to the attributes listed in [`:help :command-complete`](https://neovim.io/doc/user/map.html#:command-complete).

```lua
vim.api.nvim_create_user_command('Upper', function() end, {
    nargs = 1,
    complete = function(ArgLead, CmdLine, CursorPos)
        -- return completion candidates as a list-like table
        return { 'foo', 'bar', 'baz' }
    end,
})
```

Buffer-local user commands also take a buffer number as their first argument. This is an advantage over `-buffer` which can only define a command for the current buffer.

```lua
vim.api.nvim_buf_create_user_command(4, 'Upper', function() end, {})
```

`vim.api.nvim_del_user_command()` takes a command name.

```lua
vim.api.nvim_del_user_command('Upper')
-- :delcommand Upper
```

Again, `vim.api.nvim_buf_del_user_command()`, takes a buffer number as its first argument, with `0` representing the current buffer.

```lua
vim.api.nvim_buf_del_user_command(4, 'Upper')
```

자세한 정보:
- [`:help nvim_create_user_command()`](https://neovim.io/doc/user/api.html#nvim_create_user_command())
- [`:help 40.2`](https://neovim.io/doc/user/usr_40.html#40.2)
- [`:help command-attributes`](https://neovim.io/doc/user/map.html#command-attributes)

### Caveats

The `-complete=custom` attribute automatically filters completion candidates and has built-in wildcard ([`:help wildcard`](https://neovim.io/doc/user/editing.html#wildcard)) support:

```vim
function! s:completion_function(ArgLead, CmdLine, CursorPos) abort
    return join([
        \ 'strawberry',
        \ 'star',
        \ 'stellar',
        \ ], "\n")
endfunction

command! -nargs=1 -complete=custom,s:completion_function Test echo <q-args>
" Typing `:Test st[ae]<Tab>` returns "star" and "stellar"
```

Passing a Lua function to `complete` makes it behave like `customlist` which leaves filtering up to the user:

```lua
vim.api.nvim_create_user_command('Test', function() end, {
    nargs = 1,
    complete = function(ArgLead, CmdLine, CursorPos)
        return {
            'strawberry',
            'star',
            'stellar',
        }
    end,
})

-- Typing `:Test z<Tab>` returns all the completion results because the list was not filtered
```

## Defining autocommands

(this section is a work in progress)

Neovim 0.7.0 has API functions for autocommands. See `:help api-autocmd` for details

- [Pull request #14661](https://github.com/neovim/neovim/pull/14661) (lua: autocmds take 2)

## Defining highlights

(this section is a work in progress)

Neovim 0.7.0 has API functions for highlight groups. 자세한 정보:

- [`:help nvim_set_hl()`](https://neovim.io/doc/user/api.html#nvim_set_hl())
- [`:help nvim_get_hl_by_id()`](https://neovim.io/doc/user/api.html#nvim_get_hl_by_id())
- [`:help nvim_get_hl_by_name()`](https://neovim.io/doc/user/api.html#nvim_get_hl_by_name())

## General tips and recommendations

### Reloading cached modules

In Lua, the `require()` function caches modules. This is a good thing for performance, but it can make working on plugins a bit cumbersome because modules are not updated on subsequent `require()` calls.

If you'd like to refresh the cache for a particular module, you have to modify the `package.loaded` global table:

```lua
package.loaded['modname'] = nil
require('modname') -- loads an updated version of module 'modname'
```

The [nvim-lua/plenary.nvim](https://github.com/nvim-lua/plenary.nvim) plugin has a [custom function](https://github.com/nvim-lua/plenary.nvim/blob/master/lua/plenary/reload.lua) that does this for you.

### Don't pad Lua strings!

When using double bracketed strings, resist the temptation to pad them! While it is fine to do in contexts where spaces are ignored, it can cause hard to debug issues when whitespace is significant:

```lua
vim.api.nvim_set_keymap('n', '<Leader>f', [[ <Cmd>call foo()<CR> ]], {noremap = true})
```

In the above example, `<Leader>f` is mapped to `<Space><Cmd>call foo()<CR><Space>` instead of `<Cmd>call foo()<CR>`.

### 알림s about Vimscript <-> Lua type conversion

#### Converting a variable creates a copy:
You can't directly interact with the reference to a Vim object from Lua or a Lua object from Vimscript.  
For example, the `map()` function in Vimscript modifies a variable in place:

```vim
let s:list = [1, 2, 3]
let s:newlist = map(s:list, {_, v -> v * 2})

echo s:list
" [2, 4, 6]
echo s:newlist
" [2, 4, 6]
echo s:list is# s:newlist
" 1
```

Using this function from Lua creates a copy instead:

```lua
local tbl = {1, 2, 3}
local newtbl = vim.fn.map(tbl, function(_, v) return v * 2 end)

print(vim.inspect(tbl)) -- { 1, 2, 3 }
print(vim.inspect(newtbl)) -- { 2, 4, 6 }
print(tbl == newtbl) -- false
```

#### Conversion is not always possible
This mostly affects functions and tables:

Lua tables that are a mix between a List and a Dictionary can't be converted:

```lua
print(vim.fn.count({1, 1, number = 1}, 1))
-- E5100: Cannot convert given lua table: table should either have a sequence of positive integer keys or contain only string keys
```

While you can call Vim functions in Lua with `vim.fn`, you can't hold references to them. This can cause surprising behaviors:

```lua
local FugitiveHead = vim.fn.funcref('FugitiveHead')
print(FugitiveHead) -- vim.NIL

vim.cmd("let g:test_dict = {'test_lambda': {-> 1}}")
print(vim.g.test_dict.test_lambda) -- nil
print(vim.inspect(vim.g.test_dict)) -- {}
```

Passing Lua functions to Vim functions is OK, storing them in Vim variables is not (fixed in Neovim 0.7.0+):

```lua
-- This works:
vim.fn.jobstart({'ls'}, {
    on_stdout = function(chan_id, data, name)
        print(vim.inspect(data))
    end
})

-- This doesn't:
vim.g.test_dict = {test_lambda = function() return 1 end} -- Error: Cannot convert given lua type
```

알림 however that doing the same from Vimscript with `luaeval()` **does** work:

```vim
let g:test_dict = {'test_lambda': luaeval('function() return 1 end')}
echo g:test_dict
" {'test_lambda': function('<lambda>4714')}
```

#### Vim booleans
A common pattern in Vim scripts is to use `1` or `0` instead of proper booleans. Indeed, Vim did not have a separate boolean type until version 7.4.1154.

Lua booleans are converted to actual booleans in Vimscript, not numbers:

```vim
lua vim.g.lua_true = true
echo g:lua_true
" v:true
lua vim.g.lua_false = false
echo g:lua_false
" v:false
```

### Setting up linters/language servers

If you're using linters and/or language servers to get diagnostics and autocompletion for Lua projects, you may have to configure Neovim-specific settings for them. Here are a few recommended settings for popular tools:

#### luacheck

You can get [luacheck](https://github.com/mpeterv/luacheck/) to recognize the `vim` global by putting this configuration in `~/.luacheckrc` (or `$XDG_CONFIG_HOME/luacheck/.luacheckrc`):

```lua
globals = {
    "vim",
}
```

The [Alloyed/lua-lsp](https://github.com/Alloyed/lua-lsp/) language server uses `luacheck` to provide linting and reads the same file.

For more information on how to configure `luacheck`, please refer to its [documentation](https://luacheck.readthedocs.io/en/stable/config.html)

#### sumneko/lua-language-server

The [nvim-lspconfig](https://github.com/neovim/nvim-lspconfig/) repository contains [instructions to configure sumneko/lua-language-server](https://github.com/neovim/nvim-lspconfig/blob/master/doc/server_configurations.md#sumneko_lua) (the example uses the built-in LSP client but the configuration should be identical for other LSP client implementations).

For more information on how to configure [sumneko/lua-language-server](https://github.com/sumneko/lua-language-server/) see ["Setting"](https://github.com/sumneko/lua-language-server/wiki/Setting)

#### coc.nvim

The [rafcamlet/coc-nvim-lua](https://github.com/rafcamlet/coc-nvim-lua/) completion source for [coc.nvim](https://github.com/neoclide/coc.nvim/) provides completion items for the Neovim stdlib.

### Debugging Lua code

You can debug Lua code running in a separate Neovim instance with [jbyuki/one-small-step-for-vimkind](https://github.com/jbyuki/one-small-step-for-vimkind)

The plugin uses the [Debug Adapter Protocol](https://microsoft.github.io/debug-adapter-protocol/). Connecting to a debug adapter requires a DAP client like [mfussenegger/nvim-dap](https://github.com/mfussenegger/nvim-dap/) or [puremourning/vimspector](https://github.com/puremourning/vimspector/).

### Debugging Lua mappings/commands/autocommands

The `:verbose` command allows you to see where a mapping/command/autocommand was defined:

```vim
:verbose map m
```

```text
n  m_          * <Cmd>echo 'example'<CR>
        Last set from ~/.config/nvim/init.vim line 26
```

By default, this feature is disabled in Lua for performance reasons. You can enable it by starting Neovim with a verbose level greater than 0:

```sh
nvim -V1
```

자세한 정보:
- [`:help 'verbose'`](https://neovim.io/doc/user/options.html#'verbose')
- [`:help -V`](https://neovim.io/doc/user/starting.html#-V)
- [neovim/neovim#15079](https://github.com/neovim/neovim/pull/15079)

### Testing Lua code

- [plenary.nvim: test harness](https://github.com/nvim-lua/plenary.nvim/#plenarytest_harness)
- [notomo/vusted](https://github.com/notomo/vusted)

### Using Luarocks packages

[wbthomason/packer.nvim](https://github.com/wbthomason/packer.nvim) supports Luarocks packages. Instructions for how to set this up are available in the [README](https://github.com/wbthomason/packer.nvim/#luarocks-support)

## Miscellaneous

### vim.loop

`vim.loop` is the module that exposes the LibUV API. Some resources:

- [Official documentation for LibUV](https://docs.libuv.org/en/v1.x/)
- [Luv documentation](https://github.com/luvit/luv/blob/master/docs.md)
- [teukka.tech - Using LibUV in Neovim](https://teukka.tech/posts/2020-01-07-vimloop/)

자세한 정보:
- [`:help vim.loop`](https://neovim.io/doc/user/lua.html#vim.loop)

### vim.lsp

`vim.lsp` is the module that controls the built-in LSP client. The [neovim/nvim-lspconfig](https://github.com/neovim/nvim-lspconfig/) repository contains default configurations for popular language servers.

The behavior of the client can be configured using "lsp-handlers". For more information:
- [`:help lsp-handler`](https://neovim.io/doc/user/lsp.html#lsp-handler)
- [neovim/neovim#12655](https://github.com/neovim/neovim/pull/12655)
- [How to migrate from diagnostic-nvim](https://github.com/nvim-lua/diagnostic-nvim/issues/73#issue-737897078)

You may also want to take a look at [plugins built around the LSP client](https://github.com/rockerBOO/awesome-neovim#lsp)

자세한 정보:
- [`:help lsp`](https://neovim.io/doc/user/lsp.html#LSP)

### vim.treesitter

`vim.treesitter` is the module that controls the integration of the [Tree-sitter](https://tree-sitter.github.io/tree-sitter/) library in Neovim. If you want to know more about Tree-sitter, you may be interested in this [presentation (38:37)](https://www.youtube.com/watch?v=Jes3bD6P0To).

The [nvim-treesitter](https://github.com/nvim-treesitter/) organisation hosts various plugins taking advantage of the library.

자세한 정보:
- [`:help lua-treesitter`](https://neovim.io/doc/user/treesitter.html#lua-treesitter)

### Transpilers

One advantage of using Lua is that you don't actually have to write Lua code! There is a multitude of transpilers available for the language.

- [Moonscript](https://moonscript.org/)

Probably one of the most well-known transpilers for Lua. Adds a lots of convenient features like classes, list comprehensions or function literals. The [svermeulen/nvim-moonmaker](https://github.com/svermeulen/nvim-moonmaker) plugin allows you to write Neovim plugins and configuration directly in Moonscript.

- [Fennel](https://fennel-lang.org/)

A lisp that compiles to Lua. You can write configuration and plugins for Neovim in Fennel with the [Olical/aniseed](https://github.com/Olical/aniseed) or the [Hotpot](https://github.com/rktjmp/hotpot.nvim) plugin. Additionally, the [Olical/conjure](https://github.com/Olical/conjure) plugin provides an interactive development environment that supports Fennel (among other languages).

- [Teal](https://github.com/teal-language/tl)

The name Teal comes from pronouncing TL (typed lua).  This is exactly what it tries to do - add strong typing to lua while otherwise remaining close to standard lua syntax.  The [nvim-teal-maker](https://github.com/svermeulen/nvim-teal-maker) plugin can be used to write Neovim plugins or configuration files directly in Teal

Other interesting projects:
- [TypeScriptToLua/TypeScriptToLua](https://github.com/TypeScriptToLua/TypeScriptToLua)
- [Haxe](https://haxe.org/)
- [SwadicalRag/wasm2lua](https://github.com/SwadicalRag/wasm2lua)
- [hengestone/lua-languages](https://github.com/hengestone/lua-languages)
