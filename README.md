# Contas Claude (instaladores)

App da Seazone para o pool de contas do claude-switcher: mostra todas as contas com o uso de cada
uma, troca de conta sozinho quando a sua esgota (conferindo ao vivo se a nova tem crédito) e acorda
as sessões do Claude Code que pararam por limite. Sem terminal.

Este repositório só guarda os instaladores (releases); o código fica em `seazone-tech/switcher-painel`.

## Instalar

Os links abaixo apontam sempre para a versão mais recente.

- **Windows**: baixe e clique duas vezes em
  [ContasClaude-setup-windows.exe](https://github.com/seazone-tech/switcher-painel-dist/releases/latest/download/ContasClaude-setup-windows.exe).
  Instala para o seu usuário, sem administrador, e cria o atalho "Contas Claude" no Menu Iniciar.
- **macOS (chip Apple, M1 ou mais novo)**: baixe
  [ContasClaude-macos.dmg](https://github.com/seazone-tech/switcher-painel-dist/releases/latest/download/ContasClaude-macos.dmg),
  arraste o Contas Claude para a pasta Aplicativos e abra de lá. Na primeira vez, botão direito →
  Abrir (o app não é assinado pela Apple; só nessa primeira abertura).
- **Linux**: baixe
  [ContasClaude-linux.AppImage](https://github.com/seazone-tech/switcher-painel-dist/releases/latest/download/ContasClaude-linux.AppImage),
  dê permissão de execução (`chmod +x ContasClaude-linux.AppImage`) e abra.

## Primeira abertura

1. Clique em "Entrar com a conta Google" e entre com a conta @seazone.com.br.
2. O app prepara o resto sozinho: heartbeat a cada 15 min sem terminal, conta do pool e retomada das
   sessões do Claude Code. Se a máquina tinha o switcher antigo de terminal, o app tira o agendamento
   dele (era ele que piscava um terminal a cada 15 min).
3. O ícone fica na bandeja (Windows e Linux) ou na barra de menus (macOS); fechar a janela só recolhe.
   "Iniciar com o computador" fica no próprio painel.

O app confere este repositório e se atualiza sozinho.

## Tirar o resto do switcher antigo de terminal

O app já remove o agendamento antigo ao preparar a máquina. Para tirar o que sobra (o comando
`switcher`, o `.cmd` e a pasta clonada), cole isto no Claude Code:

```
Desinstale o switcher ANTIGO de terminal (claude-switcher) desta máquina, sem mexer na pasta ~/.claude-switcher nem em ~/.claude/.credentials.json (guardam a sessão e a conta, que o app Contas Claude reaproveita). Faça nesta ordem e me mostre o que fez:
1. Heartbeat agendado antigo: se o comando `switcher` existir, rode `switcher schedule --remove`. Se não existir, remova à mão. Windows: `schtasks /query /tn claude-switcher-heartbeat /v /fo LIST` e apague com `schtasks /delete /tn claude-switcher-heartbeat /f` SÓ se a ação NÃO apontar para ContasClaude.exe ou app.py (nesse caso a tarefa já é do app novo e fica). macOS: `launchctl bootout gui/$(id -u)/com.seazone.claude-switcher-heartbeat` e apague ~/Library/LaunchAgents/com.seazone.claude-switcher-heartbeat.plist. Linux: `systemctl --user disable --now claude-switcher-heartbeat.timer` e apague ~/.config/systemd/user/claude-switcher-heartbeat.timer e .service.
2. Apague o comando antigo: ~/.local/bin/switcher e ~/.local/bin/switcher.cmd. No Windows, apague também %LOCALAPPDATA%\claude-switcher\heartbeat.cmd e heartbeat.pyw, se existirem.
3. Apague a pasta clonada da API, se existir: ~/claude-switcher-api.
4. Não apague ~/.claude-switcher nem ~/.claude/.credentials.json. No fim, liste o que removeu e o que não encontrou.
```

## Se algo der errado

O registro do app fica em `~/.claude-switcher/painel.log` (e `painel-casca.log` para a casca).
Problemas e pedidos: fale com o Nathan (Jurídico).
