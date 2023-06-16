<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

Recomenda-se instalar nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) primeiro e, em seguida `direnv allow` depois de entrar no diretório ( [o .envrc](https://github.com/xxai-art/doc/blob/main/.envrc) será executado automaticamente depois de entrar no diretório).

O significado é: tradução chinesa para japonês, coreano, inglês, tradução inglesa para todos os outros idiomas. Se você deseja oferecer suporte apenas para chinês e inglês, basta escrever `zh: en` .

O significado é: tradução chinesa para japonês, coreano, inglês, tradução inglesa para todos os outros idiomas. Se você deseja oferecer suporte apenas para chinês e inglês, basta escrever `zh: en` .

* [código de front-end](https://github.com/xxai-art/web)
* [Pacotes de idiomas para o site como um todo](https://github.com/xxai-art/web/tree/main/i18n)
* [Pacotes de idiomas para módulos de login](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Documentação multilíngue do site](https://github.com/xxai-doc)

A linguagem de programação front-end é [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , que adiciona alguns recursos com base na sintaxe coffeescript, consulte [./coffee_plus.md](./coffee_plus.md) .

## Internacionalização de sites e documentos

Desenvolva os 3 projetos a seguir

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  O sufixo é `.mdt` , você pode usar a sintaxe similar a `<+ ./coffee_plus/import.js>` para referenciar arquivos externos, e gerar markdown com o sufixo `.md` .

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  A tradução Markdown não traduzirá códigos e links e armazenará em cache as frases traduzidas. Se a tradução for modificada, mas o texto original não for modificado, executá-la novamente não substituirá a modificação da tradução.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  Arquivos de idioma para traduzir sites gerados `yaml` .

### Instruções de Automação de Tradução de Documentos

Veja o repositório de código [xxai-art/doc](https://github.com/xxai-art/doc)

Recomenda-se instalar nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) primeiro e, em seguida `direnv allow` depois de entrar no diretório ( [o .envrc](https://github.com/xxai-art/doc/blob/main/.envrc) será executado automaticamente depois de entrar no diretório).

Para evitar a grande base de código traduzida em centenas de idiomas, criei uma base de código separada para cada idioma e criei uma organização para armazenar a base de código

Definir a variável de ambiente `GITHUB_ACCESS_TOKEN` e, em seguida, executar [create.github.coffee](https://github.com/xxai-art/doc/blob/main/create.github.coffee) criará automaticamente o repositório de código.

Claro, você também pode colocá-lo em uma base de código.

Referência de script de tradução [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

O código do script é interpretado da seguinte forma:

[bunx](https://bun.sh/docs/cli/bunx) é um substituto para npx, que é mais rápido. Obviamente, se você não tiver o bun instalado, poderá usar `npx` .

`bunx mdt zh` processa `.mdt` no diretório zh como `.md` , veja os 2 arquivos vinculados abaixo

* [coffee_plus.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [coffee_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` é o código principal para tradução (se você tiver apenas `nodejs` instalado, mas `bun` e `direnv` não estiverem instalados, você também pode executar `npx i18n` para traduzir).

Ele irá analisar [i18n.yml](https://github.com/xxai-art/doc/blob/main/i18n.yml) , a configuração de `i18n.yml` neste documento é a seguinte:

```
en:
zh: ja ko en
```

O significado é: tradução chinesa para japonês, coreano, inglês, tradução inglesa para todos os outros idiomas. Se você deseja oferecer suporte apenas para chinês e inglês, basta escrever `zh: en` .

O último é [gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) , que extrai o conteúdo entre o título principal e o primeiro subtítulo do `README.md` de cada idioma para gerar uma entrada `README.md` . O código é muito simples, você mesmo pode ver.

A API do Google é usada para tradução gratuita. Se você não conseguir acessar o Google, configure e defina um proxy, como:

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

O script de tradução irá gerar um cache traduzido no diretório `.i18n` , verifique-o com `git status` e adicione-o ao repositório de código para evitar traduções repetidas.

Execute `bunx i18n` sempre que modificar a tradução para atualizar o cache.

Se o texto original e a tradução forem modificados ao mesmo tempo, o cache ficará confuso, portanto, se você quiser modificar, poderá modificar apenas um e, em seguida, execute `bunx i18n` para atualizar o cache.
