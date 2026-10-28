# Claude Switcher (instaladores)

App da Seazone para o pool de contas do claude-switcher: mostra todas as contas com o uso de cada
uma, troca de conta sozinho quando a sua esgota (conferindo ao vivo se a nova tem crédito) e acorda
as sessões do Claude Code que pararam por limite. Sem terminal.

Este repositório só guarda os instaladores (releases); o código fica em `seazone-tech/switcher-painel`.
Até a versão 1.1.3 o app se chamava "Contas Claude"; quem tem essa versão recebe o nome novo pela
atualização automática.

## Instalar

Os links abaixo apontam sempre para a versão mais recente.

- **Windows**: baixe e clique duas vezes em
  [ClaudeSwitcher-setup-windows.exe](https://github.com/seazone-tech/switcher-painel-dist/releases/latest/download/ClaudeSwitcher-setup-windows.exe).
  Instala para o seu usuário, sem administrador, e cria o atalho "Claude Switcher" no Menu Iniciar.
- **macOS (chip Apple, M1 ou mais novo)**: baixe
  [ClaudeSwitcher-macos.dmg](https://github.com/seazone-tech/switcher-painel-dist/releases/latest/download/ClaudeSwitcher-macos.dmg),
  arraste o Claude Switcher para a pasta Aplicativos e abra de lá. O app não é notarizado pela Apple,
  então na primeira abertura o macOS avisa que não pôde verificá-lo: clique em "Concluído", abra
  Ajustes do Sistema → Privacidade e Segurança, role até o aviso do Claude Switcher e clique em
  "Abrir Mesmo Assim" (pede a senha do Mac). Só nessa primeira vez. Mac Intel não tem instalador.
- **Linux**: baixe
  [ClaudeSwitcher-linux.AppImage](https://github.com/seazone-tech/switcher-painel-dist/releases/latest/download/ClaudeSwitcher-linux.AppImage),
  dê permissão de execução (`chmod +x ClaudeSwitcher-linux.AppImage`) e abra.

## Primeira abertura

1. Clique em "Entrar com a conta Google" e entre com a conta @seazone.com.br. Quem já usava o
   switcher de terminal entra direto: a sessão dele vale para o app.
2. O app prepara o resto sozinho: heartbeat a cada 15 min sem terminal, conta do pool e retomada das
   sessões do Claude Code. Se a máquina tinha o switcher de terminal, o app assume o lugar dele na
   mesma abertura: troca o agendamento antigo (que abria uma janela de terminal a cada 15 min) pelo
   do app e faz o comando `switcher` chamar o próprio app. Não precisa desinstalar nada.
3. O ícone fica na bandeja (Windows e Linux) ou na barra de menus (macOS); fechar a janela só recolhe.
   "Iniciar com o computador" fica no próprio painel.

O app confere este repositório e se atualiza sozinho. A pasta clonada da API do switcher
(`~/claude-switcher-api`), se existir, pode ser apagada: o app não precisa dela.

## Se algo der errado

O registro do app fica em `~/.claude-switcher/painel.log` (e `painel-casca.log` para a casca).
Problemas e pedidos: fale com o Nathan (Jurídico).
