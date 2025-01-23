# Orçamento para Loja de Computadores e Manutenção

Este repositório contém uma planilha customizável para gerenciar orçamentos de uma loja que vende e faz manutenção de computadores. O projeto é estruturado para facilitar o uso e inclui funcionalidades avançadas, como validações dinâmicas de dados e integração com dados tratados para melhorar a eficiência.

---

## ⚙️ Como Usar a Planilha

1. **Personalização Inicial**
   - Adicione a logomarca da sua loja, número de telefone e nome da loja nos campos indicados.
   - A planilha estará pronta para começar a gerar orçamentos.

2. **Gerenciamento de Itens**
   - Na coluna **Item**, clique na seta para selecionar o tipo de item. Os tipos disponíveis são:
     - `Cooler`, `Fonte`, `Formatação`, `Gabinete`, `HD`, `Manutenção`, `Memória RAM`, `Monitor`, `Montagem`, `Placa de Vídeo`, `Placa mãe`, `Processador`, `Reparo`, `Serviços em notebooks`, `SSD`, `Upgrade`.
   - Ao selecionar um tipo, a coluna **Descrição** exibirá automaticamente os itens relacionados, como marcas e especificações técnicas.

3. **Preenchimento do Orçamento**
   - Insira o **valor unitário** e a **quantidade** do item para calcular automaticamente o valor total por linha.
   - O subtotal é calculado automaticamente, e você pode aplicar **descontos** ou **acréscimos** conforme necessário.
   - O valor final do orçamento será exibido no campo **Total Geral**.

4. **Configurações Extras**
   - Atualize o campo **Orçamento válido por** com o número de dias de validade desejado (padrão: 15 dias).
   - Utilize a seção **Forma de Pagamento e Condições** para adicionar detalhes sobre o pagamento.

---

## 🛠️ Detalhes Técnicos

- **Validação de Dados Dinâmica:**
  A seleção dinâmica dos itens foi implementada usando a função `OFFSET`, permitindo que apenas as descrições relevantes apareçam com base no tipo de item selecionado:
  ```excel
  =OFFSET('Tipo Item'!A:A,,,COUNTA('Tipo Item'!A:A))


- Cálculo Dinâmico para Descrições: Para vincular os tipos de itens às suas descrições, foi utilizada a fórmula abaixo:
  ```excel
  =LET(letra,SUBSTITUTE(ADDRESS(1,MATCH(B14,Itens!$A$1:$J$1,0),4),"1",""),
     ind,INDIRECT(CONCAT("Itens!",letra,":",letra),TRUE),
     OFFSET(ind,1,,COUNTA(ind)-1))
     
- **Variável `letra`:** Identifica a coluna associada ao tipo de item selecionado (ex.: `A` para Gabinete).
- **Variável `ind`:** Define o intervalo correspondente na aba "Itens" (ex.: `A:A`).

### Estrutura dos Dados
Os dados foram tratados e organizados na aba **Itens**, separando cada categoria de item em colunas. Além disso, alguns ajustes foram feitos para padronizar as descrições:
- **HD e SSD:** Adicionada a capacidade em GB ao nome.
- **Fonte:** Adicionadas a potência em W e o tamanho (ex.: ATX).
- **Memória RAM:** Adicionados a frequência em MHz e a capacidade em GB.
- **Monitores:** Adicionadas as informações de taxa de atualização (Hz) e tamanho em polegadas.
- **Placas de Vídeo:** Adicionada a quantidade de memória VRAM (em GB).

---

## 🔄 Como Atualizar os Dados da Planilha

1. **Adicionar Novos Itens**
 - Na aba **Itens**, insira os novos produtos nas colunas correspondentes. Certifique-se de seguir o mesmo formato de descrição.
 - **Exemplo:** Para adicionar um novo SSD, insira o nome e a capacidade na coluna "SSD".

2. **Atualizar Tipos de Itens**
 - Na aba **Tipo Item**, adicione novos tipos de itens na lista. As validações serão atualizadas automaticamente.

3. **Revisar Validações**
 - Caso novos itens ou tipos sejam adicionados, revise as fórmulas para garantir que as validações dinâmicas estejam funcionando corretamente.

---

## 📄 Fontes

- **Planilha Base:**  
[Smart Planilhas - Planilha de Orçamento para Cliente](https://smartplanilhas.com.br/planilha-gratuita/planilha-de-orcamento-para-cliente/?srsltid=AfmBOoocRgxyCDTd4uHFrkTPZZlnSI_-0da_NKbevbRIqUgtpnC06lal)

- **Dataset Utilizado:**  
[Kaggle - General Computer Hardware Dataset](https://www.kaggle.com/datasets/dilshaansandhu/general-computer-hardware-dataset?select=HDDData.csv)

---

## 🖥️ Requisitos do Sistema

- Microsoft Excel (versão 2019 ou superior recomendada).

---

Este projeto foi desenvolvido para oferecer uma solução prática e eficiente para a gestão de orçamentos em lojas de informática. Sugestões e feedbacks são bem-vindos!
