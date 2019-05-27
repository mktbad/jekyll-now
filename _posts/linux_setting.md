+ x11
    + .ssh/configでForwardX11 yes ForwardX11Trusted yes
    + /etc/ssh/sshd_configでX11Forwarding yes　X11DisplayOffset 10　＝＞　いらない説
    + sudo service sshd restart
    + VcXsrvが自動的に起動されるようにする
    + sudo apt install x11-appsしてxeyesで動作確認
    + https://www.atmarkit.co.jp/ait/articles/1812/06/news040.html
    + http://kb.tokyo.optim.co.jp/open.knowledge/view/32?offset=0&keyword=forwarding (configの方法を取る)
    この作業以前に作ったtmuxのセッションだとx11サーバーが機能しない

+ python
~~~
cd ~
sudo apt install -y gcc make libssl-dev libbz2-dev libreadline-dev libsqlite3-dev zlib1g-dev
git clone https://github.com/pyenv/pyenv.git ~/.pyenv
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bash_profile
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bash_profile
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n eval "$(pyenv init -)"\nfi' >> ~/.bash_profile
source ~/.bash_profile
git clone https://github.com/pyenv/pyenv-virtualenv.git $(pyenv root)/plugins/pyenv-virtualenv
echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bash_profile
source ~/.bash_profile
pyenv install anaconda3-4.4.0
pyenv global anaconda3-4.4.0 
cd ~/target_dir
conda create -n env python=3.6
pyenv local anaconda3-4.4.0/envs/env
conda install -c conda-forge opencv
~~~
~~~
# code-checkerを入れる＝＞autopep8 --in-place --aggressive --aggressive
pip install flake8
pip install --upgrade autopep8　
# pathogen.vimを入れる
mkdir -p ~/.vim/autoload ~/.vim/bundle && \
curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim
echo "execute pathogen#infect()" >> ~/.vimrc
# vim-flake8を入れる
git clone https://github.com/nvie/vim-flake8.git ~/.vim/bundle
~~~