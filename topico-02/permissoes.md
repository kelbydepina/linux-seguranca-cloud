# Permissões aplicadas

## Ambiente utilizado
VM local (VirtualBox) com Ubuntu Server 26.04.1 LTS.

## Utilizador e grupos
    whoami: kelby
    id: uid=1000(kelby) gid=1000(kelby) groups=1000(kelby),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),100(users),101(lxd)
    groups: kelby adm cdrom sudo dip plugdev users lxd

## Ficheiros criados
- publico.txt: ficheiro de texto com conteúdo que pode ser lido por qualquer utilizador.
- restrito.txt: ficheiro de texto com conteúdo que só deve ser lido pelo dono e pelo grupo.
- script.sh: pequeno script em bash que escreve o nome do utilizador que o executa.

## Permissões aplicadas
| Ficheiro | Permissão | Justificação |
|---|---:|---|
| publico.txt | 644 | O dono lê e escreve; grupo e outros só leem. Adequado para conteúdo público que ninguém além do dono deve alterar. |
| restrito.txt | 640 | O dono lê e escreve, o grupo só lê e os outros não têm qualquer acesso. Protege conteúdo sensível. |
| script.sh | u+x | Só o dono ganha permissão de execução. Sem ela o script não corre (Permission denied). |

## Relação com o princípio do menor privilégio
O princípio do menor privilégio diz que cada utilizador ou processo deve ter apenas as permissões necessárias para a sua função. Dar permissões totais (777) a todos permitiria que qualquer utilizador lesse, alterasse ou executasse qualquer ficheiro, o que aumenta o risco de erros, de fugas de informação e de abuso se uma conta for comprometida. Com 644, 640 e u+x, cada ficheiro tem só o acesso de que precisa.
