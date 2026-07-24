## Cores no prompt do Bash

### 1. Usuário (Verde)
```bash
cat << 'EOF' > ~/.bashrc
[[ $- != *i* ]] && return
PS1='\[\e[1;32m\]\u@\h \[\e[1;34m\]\W\[\e[0m\] \$ '
alias ls='ls --color=auto'
alias grep='grep --color=auto'
alias ip='ip -color=auto'
EOF
source ~/.bashrc

```

### 2. Root (Vermelho)

```bash
sudo bash -c "cat << 'EOF' > /root/.bashrc
[[ \$- != *i* ]] && return
PS1='\[\e[1;31m\]\u@\h \[\e[1;34m\]\W\[\e[0m\] # '
alias ls='ls --color=auto'
alias grep='grep --color=auto'
alias ip='ip -color=auto'
EOF"

```

### 3. Perfil de Login (Root)

Garante a leitura do `.bashrc` em acessos via `sudo -i` ou `su -`.

```bash
sudo bash -c "cat << 'EOF' > /root/.bash_profile
[[ -f ~/.bashrc ]] && source ~/.bashrc
EOF"

```
