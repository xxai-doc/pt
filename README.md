<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.art

Parte do código do site é de código aberto, bem-vindo para ajudar a otimizar a tradução.

## código de front-end

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
