# pyenv
see http://qiita.com/Kodaira_/items/feadfef9add468e3a85b

pyenv is a manager for python environment.

## Install
```
git clone https://github.com/yyuu/pyenv.git ~/.pyenv
```

Add following to `.zshrc` or `.bashrc`

```
export PYENV_ROOT=$HOME/.pyenv
export PATH=$PYENV_ROOT/bin:$PATH
eval $(pyenv init -)
```

Install specific version of python
```
pyenv install 2.7.9
```

## Switch python version
```
pyenv global 2.7.9
```

The setting is stored even though terminal process is finished.
