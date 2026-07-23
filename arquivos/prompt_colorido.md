## Cores no prompt do Bash (Usuário e Root)

### 1. Usuário (Verde/Azul)
```bash
cat << 'EOF' > ~/.bashrc
# ~/.bashrc

[[ $- != *i* ]] && return

PS1='[\[\e[1;32m\]\u@\h \[\e[1;34m\]\W\[\e[0m\]]\$ '

alias ls='ls --color=auto'
alias grep='grep --color=auto'
alias ip='ip -color=auto'
EOF

source ~/.bashrc

```

### 2. Root (Vermelho/Azul)

```bash
sudo bash -c "cat << 'EOF' > /root/.bashrc
# /root/.bashrc

[[ \$- != *i* ]] && return

PS1='[\[\e[1;31m\]\u@\h \[\e[1;34m\]\W\[\e[0m\]]# '

alias ls='ls --color=auto'
alias grep='grep --color=auto'
alias ip='ip -color=auto'
EOF"

```

### 3. Perfil de Login (Root)

Garante a leitura do `.bashrc` em acessos via `sudo -i` ou `su -`.

```bash
sudo bash -c "cat << 'EOF' > /root/.bash_profile
if [ -f ~/.bashrc ]; then
    source ~/.bashrc
fi
EOF"

```
