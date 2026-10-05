Claro — aqui vai um `.md` pronto, com cara de material de aula, simulando uma sessão prática de **Git: `status`, `diff` e `commit`**.

 Aula prática — Git: Status, Diff e Commit

# 📚 Aula prática — Git: `status`, `diff` e `commit`

 > **Objetivo:** entender o fluxo básico de alterações no Git e aprender a inspecionar, preparar e registrar mudanças.

---

 ## 🧠 O cenário

 Imagine que temos um projeto chamado `meu-projeto`.

 A estrutura inicial é:

```
meu-projeto/
├── README.md
├── index.html
└── style.css
```

 Tudo está sincronizado e nosso repositório está limpo.

---

 # 1\. 🔍 Verificando o estado do projeto

 Antes de fazer qualquer coisa, podemos perguntar ao Git:

```
git status
```

 Resultado:

```
On branch main
nothing to commit, working tree clean
```

 Isso significa:

 - Estamos na branch `main`;
- Não existem alterações pendentes;
- O diretório de trabalho está limpo.

---

 # 2\. ✏️ Fazendo uma alteração

 Vamos modificar o `index.html`.

 Antes:

```
<h1>Olá, mundo!</h1>
```

 Depois:

```
<h1>Olá, Git!</h1>
```

 Agora temos uma alteração que ainda não foi registrada pelo Git.

 Vamos conferir:

```
git status
```

 Resultado:

```
On branch main
Changes not staged for commit:

  modified:   index.html
```

 > 💡 O Git percebeu que o arquivo mudou, mas ainda não estamos preparando essa alteração para um commit.

---

 # 3\. 🔎 Investigando a alteração com `git diff`

 Agora queremos descobrir **exatamente o que mudou**.

```
git diff
```

 O Git pode mostrar:

```
diff --git a/index.html b/index.html
index 1234567..abcdefg 100644
--- a/index.html
+++ b/index.html
@@ -1 +1 @@
-<h1>Olá, mundo!</h1>
+<h1>Olá, Git!</h1>
```

 ### Como interpretar?

 | Símbolo | Significado |
| --- | --- |
| `-` | linha removida |
| `+` | linha adicionada |
| `---` | arquivo original |
| `+++` | arquivo modificado |

Nesse caso:

```
-<h1>Olá, mundo!</h1>
+<h1>Olá, Git!</h1>
```

 Podemos ler como:

 > ❌ Removemos `Olá, mundo!`\
>  ✅ Adicionamos `Olá, Git!`

---

 # 4\. 📦 Preparando a alteração

 Antes de criar o commit, colocamos a alteração na **staging area**:

```
git add index.html
```

 Agora podemos verificar novamente:

```
git status
```

 Resultado:

```
On branch main
Changes to be committed:

  modified:   index.html
```

 Observe a diferença:

 ### Antes

```
Changes not staged for commit
```

 ### Depois do `git add`

```
Changes to be committed
```

---

 # 5\. 🔬 Conferindo o que será commitado

 Podemos usar:

```
git diff --staged
```

 Agora o Git mostra as alterações que estão **preparadas para entrar no próximo commit**:

```
diff --git a/index.html b/index.html
index 1234567..abcdefg 100644
--- a/index.html
+++ b/index.html
@@ -1 +1 @@
-<h1>Olá, mundo!</h1>
+<h1>Olá, Git!</h1>
```

 > 💡 Essa é uma ótima prática antes de fazer um commit: conferir exatamente o que está sendo registrado.

---

 # 6\. 💾 Criando o commit

 Agora podemos registrar a alteração:

```
git commit -m "Atualiza mensagem do título"
```

 O Git responde algo parecido com:

```
[main abc1234] Atualiza mensagem do título
 1 file changed, 1 insertion(+), 1 deletion(-)
```

 🎉 Pronto!

 A alteração agora faz parte do histórico do repositório.

---

 # 7\. 🧹 Verificando novamente

 Vamos executar:

```
git status
```

 Resultado:

```
On branch main
nothing to commit, working tree clean
```

 Nosso fluxo terminou.

---

 # 🔄 O fluxo completo

 Podemos resumir tudo assim:

```
        ✏️ Alteração
             │
             ▼
      ┌─────────────┐
      │ git status  │
      └──────┬──────┘
             │
             ▼
       🔎 git diff
             │
             ▼
        git add .
             │
             ▼
    🔬 git diff --staged
             │
             ▼
     git commit -m "..."
             │
             ▼
      🧹 git status
             │
             ▼
       Working tree
          clean ✅
```

---

 # 🧪 Exercício prático

 Agora é sua vez!

 ## Passo 1

 Crie ou altere um arquivo:

```
echo "# Meu projeto" > README.md
```

 ## Passo 2

 Verifique o estado:

```
git status
```

 ## Passo 3

 Veja a diferença:

```
git diff
```

 > ⚠️ Se o arquivo for novo e ainda não estiver sendo rastreado, `git diff` pode não mostrar seu conteúdo.

 ## Passo 4

 Adicione o arquivo:

```
git add README.md
```

 ## Passo 5

 Confira o que está preparado:

```
git diff --staged
```

 ## Passo 6

 Crie o commit:

```
git commit -m "Adiciona README do projeto"
```

 ## Passo 7

 Confirme:

```
git status
```

 Resultado esperado:

```
nothing to commit, working tree clean
```

---

 # 📝 Resumo da aula

 | Comando | Para que serve |
| --- | --- |
| `git status` | Ver o estado atual do repositório |
| `git diff` | Ver alterações ainda não adicionadas |
| `git add` | Colocar alterações na staging area |
| `git diff --staged` | Ver o que será incluído no commit |
| `git commit` | Registrar as alterações no histórico |

---

 ## ⭐ Regra de ouro

 Antes de fazer um commit:

```
git status
git diff
git add .
git diff --staged
git commit -m "mensagem clara"
git status
```

 > **Veja → Entenda → Prepare → Revise → Commit.**

 Esse ciclo simples ajuda a evitar commits com alterações acidentais e torna o histórico do projeto muito mais organizado.