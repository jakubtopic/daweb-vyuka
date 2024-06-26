## Povinné čtení na doma

Díky tomu, že již ovládáte základy příkazové řádky, můžete od teď přes ni otevírat celé složky ve _VS Code_. Budete mít díky tomu větší jistotu, že jste v příkazové řádce i ve _VS Code_ ve stejné složce a zároveň tím můžete ušetřit čas při spouštění serveru a otevírání _VS Code_ zároveň.

```sh
code .
```

Příkaz `code .` spustí aplikaci _VS Code_ (v příkazové řádce se _VS Code_ jmenuje stručně `code`) a ve _VS Code_ otevře složku `.`. Tečka `.` vždy znamená _aktuální složka_ (tedy to, co vypíše příkaz `pwd` na MacOS a Linuxu nebo `cd` na Windows).

### Mac

Pokud příkazová řádka hlásí něco ve stylu `Command 'code' not found` (příkaz 'code' nenalezen), je možné, že se _VS Code_ dostatečně neintegroval při instalaci do vašeho systému. Dokončení nastavení provedete přes trojhmat ve _VS Code_ :kbd[Cmd] + :kbd[Shift] + :kbd[P]. Vysune se nástrojová paleta, ve které najděte `Shell Command: Install 'code' command in PATH` a zvolte první nalezenou položku.

::fig[nástrojová paleta]{src=assets/shell-command.png}

Od této chvíle by již v nově otevřených _Terminálech_ mělo `code .` fungovat, otevírat _VS Code_.
