## Começando
Este projeto foi forkado de [Stephan Raabe's archinstall repository](https://gitlab.com/stephan-raabe/archinstall).

Para facilitar o  início, aqui está uma lista de etapas recomendadas a seguir.

O script solicitará algumas informações durante a instalação, mas ainda não está realizando nenhuma verificação de validação.
Para obter informações detalhadas sobre como instalar o Arch Linux, visite [Guia de instalação do Arch Linux](https://wiki.archlinux.org/title/installation_guide).

```bash
# Carregar layout do teclado (substitua de por br-abnt, es, se necessário)
loadkeys br-abnt2

# Aumentar o tamanho da fonte (opcional)
setfont ter-p20b

# Conectar à WLAN (se não for LAN)
iwctl --passphrase [senha] station wlan0 connect [rede]

# Verificar conexão com a internet
ping -c4 www.archlinux.org

# Verificar partições
lsblk

# Criar partições
cfdisk /dev/sda
# Partição 1: +800MB (para EFI)
# Partição 2: Sistema de arquivos Linux
# (Partição opcional 3 para Máquinas Virtuais)
# Escrever w, Confirmar Y

# Sincronizar pacotes
pacman -Syy

# Talvez seja necessário instalar o keyring atual do Arch Linux
# se a instalação do git falhar.
pacman -S archlinux-keyring
pacman -Syy

# Instalar git
pacman -S git

# Clonar instalação
git clone https://github.com/pedroacciainoli/archinstall
cd archinstall

# Iniciar o script
./1-install.sh
