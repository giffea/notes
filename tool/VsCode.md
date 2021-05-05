Plugin: Material Icon Theme, PHP Debug, PHP Intelephense, Vim

# setup IDE
```
  "diffEditor.ignoreTrimWhitespace": false,

  "editor.fontSize": 15,
  "editor.insertSpaces": true,
  "editor.minimap.enabled": false,
  "editor.rulers": [80, 100],
  "editor.tabSize": 4,
  "editor.wordWrap": "off",

  "python.pythonPath": "C:\\ProgramData\\Anaconda3\\pythonw.exe",

  //"php.executablePath": "C:\\php\\php-win.exe",
  "php.suggest.basic": false,
  "php.validate.executablePath": "C:\\php\\php-win.exe",
  "php.validate.run": "onSave",

  "vim.handleKeys": {
    "<C-c>": false,
    "<C-p>": false,
    "<C-v>": false,
    "<C-x>": false,
  },
  "vim.hlsearch": true,
  "vim.incsearch": true,
  "vim.normalModeKeyBindingsNonRecursive": [
    {
      "before": ["<C-q>"],
      "after": ["<C-v>"]
    }
  ],
  "vim.useCtrlKeys": true,
  "vim.visualstar": true,

  "workbench.editor.enablePreview": false,
  "workbench.iconTheme": "material-icon-theme",
  "terminal.integrated.shell.windows": "C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell.exe",
}
```
# setup debug
```
   "configurations": [
        {
            "name": "Listen for XDebug",
            "type": "php",
            "request": "launch",
            // "stopOnEntry": true,
            "port": 9000,

            // server -> local
            "pathMappings": {
                "/var/www/html/web_path": "${workspaceRoot}",
            }
        },
        {
            "name": "Launch currently open script",
            "type": "php",
            "request": "launch",
            "program": "${file}",
            "cwd": "${fileDirname}",
            "port": 9000
        }
    ]
   ```

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5ODMxMjYxOTFdfQ==
-->