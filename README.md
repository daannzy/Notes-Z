# Notes-Z
Um app simples em desenvilvimento pra treino 



# App de Notas com Salvamento Automático

Este projeto é um app simples que permite ao usuário digitar em um campo de texto multilinha e salvar o conteúdo automaticamente em um arquivo de texto no armazenamento interno do dispositivo.

---

## Configuração do Layout

- Adicionamos um `EditText` multilinha no layout.
- Definimos o ID como `edittext1`.
- Configuramos o `hint`, o tamanho e o `inputType` para texto livre.

---

## Permissões Necessárias

Para permitir que o app leia e grave arquivos no armazenamento interno, habilitamos a permissão:

WRITE_EXTERNAL_STORAGE

css
Copiar
Editar

Essa configuração foi feita em:

Project settings → Permission

yaml
Copiar
Editar

---

## Fluxo do App

### Evento `onCreate`

Ao iniciar a Activity, o app executa o seguinte comando para carregar o conteúdo do arquivo no campo de texto:

```java
setText(edittext1, FileUtil.readFile("/storage/emulated/0/MinhasNotas.txt"));
Esse comando lê o arquivo MinhasNotas.txt da raiz do armazenamento interno e exibe o conteúdo no edittext1.

Evento onTextChanged(edittext1)
Durante a digitação, o app salva automaticamente o conteúdo em tempo real com o código:

java
Copiar
Editar
FileUtil.writeFile("/storage/emulated/0/MinhasNotas.txt", getText(edittext1));
