# Modal Editing

Conventional typing and text editing require *manual input* patterns; if you want to change text, you have to use the mouse to click where you want to make changes, or press arrow keys repeatedly. When you make changes, you end up pressing \<backspace\> and \<enter\> many times to get things done. You *can* employ standard [text editing modifiers]() to make things easier, but ultimately, this still requires undue amounts of manual keypresses to make things happen.

Enter *modal editing*; with modal editing, you can type normally, but also switch *modes* to use your keyboard keys to perform *actions* for you at a higher level. Think about the types of tasks you're actually trying to accomplish with text and a keyboard; usually, there's some higher pattern to it like this:

1. for some amount of text (e.g. characters, words, sentences)...
2. DO something...
3. One or more times

Think about it; this pattern is evident in most text-editing tasks. You may want to:

- change a word, or many words next to each other
- delete the next sentence
- move to the next paragraph
- copy some text and paste it

This is the power of modal editing, it allows for editing text at this higher level. With just a couple keystrokes, we can perform any text task we can think of. There are many modal editors:

- **[vim](../pages/vim.md) [(docs)](https://vimhelp.org/) / [neovim](../pages/neovim.md) [(docs)](https://neovim.io/doc/user/)**
- **[emacs](../pages/emacs.md) [(docs)](https://www.gnu.org/software/emacs/manual/html_node/emacs/index.html) (editor AND environment)**
- [helix](../pages/helix.md) [(docs)](https://docs.helix-editor.com/)
- [kakoune](../pages/kakaoune.md) [(docs)](https://github.com/mawww/kakoune#basic-interaction)

`vim` and `emacs` are the most common of these more powerful editor variants. Vim is primarily an editor, but can be turned into a powerful environment with plugins. Emacs is an environment, but also features a modal editor / modal editing shortcuts, like vim. Vim shortcuts are arguably more ergonomic, but emacs can be used in 'evil mode' to get vim bindings. The choice of which (if any) editor to use amounts to personal preference. However, any modal editor will allow for faster, more powerful, and more flexible typing of the user commits to learning it.

## vim vs neovim

*Neovim* is a newer and arguably superior version of vim with very similar features, editing patterns, documentation, etc. The terms 'vim' and 'neovim', unless otherwise specified, are interchangeable within the scope of this knowledge base.

## IDE Configs

Modal editors sufficiently powerful ways of editing text / code that plugins have been developed to 'supercharge' them and expose IDE-like features within them. Once you have a strong grasp on a modal editor you like, try an IDE config for said editor (*editing* the configuration of the editor itself will be much easier if you already understand modal editing!).

### vim configs

- [spacevim](https://spacevim.org/)
- [nvchad](https://nvchad.com/)
- [lunarvim](https://www.lunarvim.org/)
- [lazyvim](https://www.lazyvim.org/)
- [astrovim](https://astronvim.com/)
- [cosmicvim](https://cosmicnvim.vercel.app/)


### emacs configs

- [spacemacs](https://www.spacemacs.org/)
- [DOOM emacs](https://github.com/doomemacs/doomemacs#introduction)
