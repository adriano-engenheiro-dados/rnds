# Artefatos da RNDS "ajustados" e empacotados em NPM Package

O conteúdo de dados enviados para a RNDS (_payload_) pode
ser validado por meio de artefatos FHIR disponibilizados pelo Ministério da Saúde (Brasil).

> O presente projeto realiza "ajustes" nos artefatos visando a produção de um NPM Package.

**IMPORTANTE**: este conteúdo não é produzido pelo Ministério da Saúde (Brasil). Nenhuma garantia é oferecida. Trata-se de um trabalho em andamento.

# Guia de mudanças

## Descrição

Mudanças foram feitas nos arquivos disponibilizados pela RNDS no [simplifier](https://simplifier.net/RedeNacionaldeDadosemSaude) para ficarem compativeis com o padrão FHIR, versão R4. Essas mudanças são mínimas e visam manter total coerência com os artefatos originais disponibilizados.

| Resource Type       | arquivo                                                                              | ERRO                                                                                                                                                                                                                              | Mudança                                                                                                                                                                                                                                                                                                        |
| ------------------- | ------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| StructureDefinition | StructureDefinition-BRAgendamentoRegulacaoAssistencial                               | Foi vinculado o Value Set http://www.saude.gov.br/fhir/r4/ValueSet/BRStatusAgendamentoRegulacaoAssistencial a variável "status" e esse Value Set não é um subconjunto do Value Set já vinculado a essa variável, do tipo required | Substitui o Value Set http://www.saude.gov.br/fhir/r4/ValueSet/BRStatusAgendamentoRegulacaoAssistencial pelo original http://hl7.org/fhir/ValueSet/appointmentstatus, tendo em vista que o Value Set brasileiro é apenas uma tradução do oficial.                                                              |
| CodeSystem          | CodeSystem-BRCondicaoMaternal                                                        | Tanto a variável "meta.lastUpdate" quanto a variável "date" estão no formato errado                                                                                                                                               | Foi adicionado "Z" ao final do valor das variáveis para indicar o fuso horário.                                                                                                                                                                                                                                 |
| ConceptMap          | ConceptMap-COVID-19VaccineMarketingAuthorizationHolderManufacturerBRImunobiologicoUE | Elemento "id" ultrapassava o limite superior de 64 caracteres                                                                                                                                                                     | Substitui o id COVID-19VaccineMarketingAuthorizationHolderManufacturerBRImunobiologicoUE por cOVID-19VaccineMarketingAuthorizationManufacturerBRImunobiologico, como "id" é um identificador lógico, servindo somente para identifica-lo no servidor local, essa mudança não o afeta.                          |
| ConceptMap          | ConceptMap-BRImunobiologicoUECOVID-19VaccineMarketingAuthorizationHolderManufacturer | Elemento "id" ultrapassava o limite superior de 64 caracteres                                                                                                                                                                     | Substitui o id ImunobiologicoUECOVID-19VaccineMarketingAuthorizationHolderM por ImunobiologicoCOVID-19VaccineMarketingAuthorizationM, como "id" é um identificador lógico, servindo somente para identifica-lo no servidor local, essa mudança não o afeta.                                                    |
| ValueSet            | ValueSet-BRGrupoAtendimento-1.0                                                      | A variável "date" esta no formato errado                                                                                                                                                                                          | Foi adicionado "Z" ao final do valor da variável para indicar o fuso horário.                                                                                                                                                                                                                                  |
| StructureDefinition | StructureDefinition-BRRegistroImunobiologicoAdministradoRotina-1.0                   | A variável "date" esta no formato errado                                                                                                                                                                                          | Foi adicionado "Z" ao final do valor da variável para indicar o fuso horário.                                                                                                                                                                                                                                  |
| ValueSet            | ValueSet-BRTipoDocumento-1.0                                                         | Duplicidade de instâncias desse Value Set                                                                                                                                                                                         | Uma dessas instâncias foi deletada.                                                                                                                                                                                                                                                                            |
| CodeSystem          | CodeSystem-BRNomeExameLOINC                                                          | Duplicidade de instâncias desse Code System                                                                                                                                                                                       | Uma dessas instâncias foi deletada.                                                                                                                                                                                                                                                                            |
| CodeSystem          | CodeSystem-BROrgaoExpedidor                                                          | Códigos duplicados, todos os códigos de um Code System devem ser únicos                                                                                                                                                           | Uma das definições dos códigos foi deleta. Code = CRBM.                                                                                                                                                                                                                                                        |
| CodeSystem          | CodeSystem-BRTipoIdentificador                                                       | Códigos duplicados, todos os códigos de um Code System devem ser únicos                                                                                                                                                           | Uma das definições dos códigos foi deleta. Code = BRACRBM.                                                                                                                                                                                                                                                     |
| CodeSystem          | CodeSystem-BRMedicamento                                                             | Códigos duplicados, todos os códigos de um Code System devem ser únicos                                                                                                                                                           | Uma das definições dos códigos foi deleta. Códigos duplicados: BR0272780U0042, BR0268345U0042, BR0328810U0087, BR0340783U0087, BR0267271U0042, BR0268084U0042, BR0340783U0062, BR0278283U0042, BR0296742, BR0273675, BR0420463, BR0292240, BR0363056U0106 e BR0449186.                                  |
| StructDefinition    | StructureDefinition-BRImunobiologicoAdministrado-2.0                                 | Foi vinculado o Value Set http://www.saude.gov.br/fhir/r4/ValueSet/BREstadoEvento-1.0 a variável "status" e esse Value Set não é um subconjunto do Value Set já vinculado a essa variável, do tipo required                       | Substituição o Value Set http://www.saude.gov.br/fhir/r4/ValueSet/BREstadoEvento-1.0 pelo original http://hl7.org/fhir/ValueSet/immunization-status. O Value Set Brasileiro engloba mais definições do que são restritas pelo conjunto do Value Set original, podendo gerar transtornos futuros.               |
| StructDefinition    | StructureDefinition-BRImunobiologicoAdministradoCampanha-2.0                         | Foi vinculado o Value Set http://www.saude.gov.br/fhir/r4/ValueSet/BREstadoEvento-1.0 a variável "status" e esse Value Set não é um subconjunto do Value Set já vinculado a essa variável, do tipo required                       | Substituição o Value Set http://www.saude.gov.br/fhir/r4/ValueSet/BREstadoEvento-1.0 pelo original http://hl7.org/fhir/ValueSet/immunization-status. O Value Set Brasileiro engloba mais definições do que são restritas pelo conjunto do Value Set original, podendo gerar transtornos futuros.               |
| StructDefinition    | StructureDefinition-BRMedicamento                                                    | Foi vinculado o Value Set http://www.saude.gov.br/fhir/r4/ValueSet/BREstadoSolicitacaoMedicamento-1.0 a variável "status" e esse Value Set não é um subconjunto do Value Set já vinculado a essa variável, do tipo required       | Substituição o Value Set http://www.saude.gov.br/fhir/r4/ValueSet/BREstadoSolicitacaoMedicamento-1.0 pelo original http://hl7.org/fhir/ValueSet/medication-status. O Value Set Brasileiro engloba mais definições do que são restritas pelo conjunto do Value Set original, podendo gerar transtornos futuros. |
| CodeSystem | CodeSystem-BRDivisaoGeograficaBrasil.json | Incompleto (apenas uma única cidade) | Atualizado com os municípios e versão para 2023-12-14 |
| ValueSet   | ValueSet-BRMunicipio-1.0                  | Asterisco (*) em versões gera erro HAPI FHIR | Fornecida versão específica 2023-12-14 |
| ValueSet | ValueSet-BRTipoDocumentoIndividuo-1.0 | Atribuindo um ValueSet (http://hl7.org/fhir/ValueSet/identifier-type) em local restrito a CodeSystem. Além disso, esse ValueSet é da versão 5.| O ValueSet foi substituido pelo CodeSystem (http://terminology.hl7.org/CodeSystem/v2-0203). Esse CodeSystem estava totalmente incluso no ValueSet e o ValueSet não incluia outro CodeSystem.

## Desenvolvedores FHIR

Os passos abaixo dependem dos aplicativos **hapi-fhir-cli.jar** disponível em https://github.com/hapifhir/hapi-fhir/releases e **fhir** disponível em 
https://fire.ly/products/firely-terminal/.

- Para gerar o NPM Package execute
```
java -jar hapi-fhir-cli.jar create-package --version 0.0.1 -v r4 --description "rnds.ajustes" --name rnds.ajustes --include-package "./*.json"
```

- Para instalar localmente o NPM Package gerado
```
fhir install rnds.ajustes-0.0.1.tgz --file
```

- Para validar artefatos (diretório exemplos)
```
java -jar validador_cli.jar exemplos\paciente-01.json -version 4.0.1 -watch-mode all -ig artefatos
```
