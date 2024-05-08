<!-- markdownlint-configure-file {
  "MD013": {
    "code_blocks": false,
    "tables": false
  },
  "MD033": false,
  "MD041": false
} -->

<h1 align="center">
  <br>
 <img src="https://github.com/Verdant31/CHIC.-Acessorios/assets/71015476/a057642a-dc3b-4e5c-b154-25ada3b6663c" alt="Chic logo" width="200">
</h1>

<p align="center">
  Esse projeto foi para uma cliente que tem uma loja de acessórios e trabalha com pontos de revenda, por motivos de contrato os repositórios ficaram como privados, porém
  fui liberado para descrever quais foram os produtos criados e o resultado.
</p>

<div align="center">
  
[Requisitos](#requsitos) •
[Proposta](#proposta) •
[Problemas encontrados](#problems) •
[Stack](#stack) 

</div>

<a name="requsitos"></a>

## Requisitos

Dentre os requisitos da cliente, se encontram:

- Impressão de códigos de barras utilizando uma impressora doméstica (Esse tipo de impressão é feito normalmente por impressoras próprias para isso)
- Gerenciamento de produtos
- Gerenciamento de condicionais (Isto é, uma porção de produtos é levada até determinado ponto de revenda, este tem por papel a venda dos produtos levados)
- Gerenciamento de revendedores
- Impressão de relatório de vendas, impressão de relatórios dos condicionais
- Plataforma para os pontos de revenda cadastrarem suas vendas a fim da proprietária poder acompanhar em tempo real como andam as vendas
- Possibilidade de utilizar um scanner para adicionar/remover produtos de condicionais e/ou solicitações de impressão
- Pesquisa de satisfação

<a name="proposta"></a>

## Proposta

Após um estudo do caso, propus o seguinte projeto:
1. Um site com acesso restrito à proprietária, nele se encontrariam todas as funcionalidades que não envolviam uma venda, ou seja: CRUD de produtos, condicionais e revendedores; impressões dos relatórios/condicionais
2. Um site para os revendedores, com autenticação exclusiva por ponto de revenda para gerenciamento de logs, contemplando as funcionalidades de cadastro de venda e balanceio de produtos
3. Um site com uma pesquisa de satisfação personalizada com o tema da loja (a cliente optou por não seguir com o tradicional forms da Google)

Logicamente, também foi necessário a criação de um backend, porém não entrei em detalhes para a cliente por motivos óbvios.

<a name="problems"></a>

## Problemas encontrados

Para este caso, existiu apenas uma funcionalidade que realmente impactou a entrega do projeto, **as impressões.**
Minha primeira tentativa de implementar as impressões foi a mais simples e a mais óbvia: utilizar uma biblioteca no próprio Frontend para cuidar disso.
**PORÉM,** dentre as bibliotecas disponíveis para geração de PDF utilizando React, todas envolvem uma perda significativa na qualidade do documento por conta da maneira a qual essa conversão é feita. Ademais, também há uma perda de qualidade (bem inferior, porem existe) na impressão de fato. Como consequência destes, o código de barras para a
etiqueta que seria utilizada ficou com uma qualidade péssima e foi rejeitado pela cliente logicamente.

### Solução
Após um tempo pesquisando, descobri que é possível utilizar a API nativa do windows para gerenciar e criar objetos de impressão, contornando completamente a perda de qualidade da conversão de HTML para PDF. Porém, como é uma API do **Sistema operacional**, foi necessário alterar o escopo do projeto.
Além da alteração de escopo, ainda houve uma dificuldade em alinhar o posicionamento das etiquetas por conta da conversão de PX para CM e da maneira como a impressora lida com isso por debaixo dos panos.

### Novo escopo
Para ter acesso ao sistema operacional, propus a transformação do site de uso da proprietária para um aplicativo Desktop, após algumas reuniões a proposta foi aceita e o projeto continuou.

<a name="stack"></a>

## Stack
Para o aplicativo desktop, tivemos:
- [Tauri Tauri + ViteJS para a interface](https://tauri.app/)
- [TailwindCSS](https://tailwindcss.com/)
- [Shadcn](https://ui.shadcn.com/)
- [AWS](https://aws.amazon.com/) (Armazenamento dos códigos de barras e imagens dos produtos)
- [MongoDB](https://www.mongodb.com/)
- [React Query](https://tanstack.com/query/v3)
- [OnScanJS](https://github.com/axenox/onscan.js/)
- [MSWinPrint.py](https://newcenturycomputers.net/projects/mswinprint.html)

*Para o site dos revendedores e para a pesquisa de satisfação, a stack foi extremamente semelhante ao do aplicativo, porém, não foi utilizado a AWS e o Tauri (Apenas Vite)

Para o backend:
- [Node + Typescript](https://nodejs.org/en)
- [Express](https://expressjs.com/)
- [AWS SDK](https://www.npmjs.com/package/@aws-sdk/client-s3)
- [Prisma](https://www.prisma.io/)
  
<a name="final"></a>
## Stack
Atualmente o contrato foi concluído e os produtos entregues, a duração do processo inteiro de implementação, prototipação, desenvolvimento, testes e refinamento durou cerca de 3 meses.


## License

MIT

---
