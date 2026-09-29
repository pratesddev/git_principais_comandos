# Principais Comandos do Git

Guia rápido com os comandos essenciais do Git e uma breve explicação de cada um.

---

## 1. Configuração inicial

| Comando | Descrição |
| --- | --- |
| `git config --global user.name "Seu Nome"` | Define o nome usado nos commits |
| `git config --global user.email "email@exemplo.com"` | Define o e-mail usado nos commits |
| `git config --global init.defaultBranch main` | Define `main` como branch padrão em novos repositórios |
| `git config --list` | Lista todas as configurações atuais |

---

## 2. Criando e obtendo repositórios

| Comando | Descrição |
| --- | --- |
| `git init` | Inicia um novo repositório Git na pasta atual |
| `git clone <url>` | Copia um repositório remoto para sua máquina |

---

## 3. Ciclo básico: alterar, preparar e salvar

| Comando | Descrição |
| --- | --- |
| `git status` | Mostra o estado dos arquivos (modificados, preparados, não rastreados) |
| `git add <arquivo>` | Adiciona um arquivo à área de preparação (*staging*) |
| `git add .` | Adiciona todas as alterações da pasta atual à área de preparação |
| `git commit -m "mensagem"` | Registra as alterações preparadas com uma mensagem descritiva |
| `git commit -am "mensagem"` | Adiciona arquivos já rastreados e faz o commit de uma vez |
| `git diff` | Mostra as diferenças ainda não preparadas |
| `git diff --staged` | Mostra as diferenças já preparadas para o commit |

---

## 4. Histórico

| Comando | Descrição |
| --- | --- |
| `git log` | Exibe o histórico completo de commits |
| `git log --oneline` | Exibe o histórico resumido, um commit por linha |
| `git log --graph --oneline --all` | Mostra o histórico como um grafo de branches |
| `git show <commit>` | Exibe os detalhes e as alterações de um commit |
| `git blame <arquivo>` | Mostra quem alterou cada linha do arquivo e quando |

---

## 5. Branches (ramificações)

| Comando | Descrição |
| --- | --- |
| `git branch` | Lista as branches locais |
| `git branch <nome>` | Cria uma nova branch |
| `git switch <nome>` | Muda para outra branch |
| `git switch -c <nome>` | Cria uma nova branch e já muda para ela |
| `git checkout <nome>` | Forma antiga de mudar de branch (ainda muito usada) |
| `git merge <nome>` | Une a branch informada à branch atual |
| `git branch -d <nome>` | Exclui uma branch já mesclada |

---

## 6. Repositórios remotos

| Comando | Descrição |
| --- | --- |
| `git remote -v` | Lista os repositórios remotos configurados |
| `git remote add origin <url>` | Conecta o repositório local a um remoto |
| `git push origin <branch>` | Envia seus commits para o repositório remoto |
| `git push -u origin <branch>` | Envia e define a branch remota como padrão de acompanhamento |
| `git pull` | Baixa e integra as alterações do remoto na branch atual |
| `git fetch` | Baixa as alterações do remoto sem integrá-las |

---

## 7. Desfazendo alterações

| Comando | Descrição |
| --- | --- |
| `git restore <arquivo>` | Descarta alterações não preparadas de um arquivo |
| `git restore --staged <arquivo>` | Remove um arquivo da área de preparação |
| `git commit --amend` | Altera o último commit (mensagem ou conteúdo) |
| `git revert <commit>` | Cria um novo commit que desfaz outro, sem reescrever o histórico |
| `git reset --soft <commit>` | Volta ao commit, mantendo as alterações preparadas |
| `git reset --hard <commit>` | Volta ao commit e **descarta** todas as alterações (cuidado!) |

---

## 8. Guardando trabalho temporariamente

| Comando | Descrição |
| --- | --- |
| `git stash` | Guarda as alterações atuais em uma pilha temporária |
| `git stash list` | Lista os stashes guardados |
| `git stash pop` | Recupera o último stash e o remove da pilha |

---

## 9. Reorganizando histórico

| Comando | Descrição |
| --- | --- |
| `git rebase <branch>` | Reaplica seus commits sobre outra base, deixando o histórico linear |
| `git cherry-pick <commit>` | Aplica na branch atual um commit específico de outra branch |

---

## 10. Tags e ignorando arquivos

| Comando | Descrição |
| --- | --- |
| `git tag v1.0.0` | Marca um commit como uma versão (ex.: lançamento) |
| `git tag` | Lista as tags existentes |
| `.gitignore` | Arquivo que lista o que o Git deve ignorar (ex.: `node_modules/`, `.env`) |

---

## Fluxo de trabalho típico

```bash
git clone <url>              # 1. obtém o projeto
git switch -c minha-feature  # 2. cria uma branch para a tarefa
# ... edita os arquivos ...
git add .                    # 3. prepara as alterações
git commit -m "Adiciona minha feature"  # 4. salva no histórico
git push -u origin minha-feature        # 5. envia para o remoto
# 6. abre um Pull Request e faz o merge
```

---

## Dicas rápidas

- Escreva mensagens de commit claras e no imperativo: *"Corrige bug no login"*.
- Faça commits pequenos e frequentes, cada um com um propósito.
- Use `git status` antes de cada commit para conferir o que está sendo salvo.
- Nunca faça commit de senhas, chaves de API ou arquivos `.env`.
- Prefira `git revert` a `git reset --hard` em branches compartilhadas.
