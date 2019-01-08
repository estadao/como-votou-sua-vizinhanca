# Como votou sua vizinhança?

Código fonte para gerar os dados da matéria [Mapa mostra como sua vizinhança votou no 2º turno e para o Congresso](https://www.estadao.com.br/infograficos/politica,mapa-mostra-como-sua-vizinhanca-votou-no-2-turno-e-para-o-congresso,944771) e conteúdos relacionados. O script principal encontra-se no diretório `code`.

## Estrutura dos demais diretórios

### ./data/censo/files

Contém arquivos de dados – não geográficos – do Censo 2010 em formato .xslx.

### ./data/geo

Essa pasta contém diversos arquivos com dados geográficos necessários para rodar o algoritmo.

#### ./data/geo/municipios-ibge

Contém um shapefile com os limites geográficos municipais mais recentes, de acordo com o IBGE.

#### ./data/geo/pontos-cidade

Trata-se de um diretório, de início vazio, que será populado com os arquivos gerados pelo script principal conforme a execução. Ele vai conter arquivos com os pontos de votação de cada cidade.

#### ./data/geo/setores-censitarios-ibge

Contém arquivos zipados com os limites dos setores censitários do IBGE, usados para estimar as características da população de cada polígono do mapa. 

#### ./data/geo/voronois-clipados

Trata-se de um diretório, de início vazio, que será populado com os arquivos gerados pelo script principal conforme a execução. Será preenchido em uma parte da função `make_voronoi_maps()`. Vai conter um arquivo para cada polígono do mapa, já cortado contra os limites geográficos da cidade. 

#### ./data/geo/voronois-finalizados

Trata-se de um diretório, de início vazio, que será populado com os arquivos gerados pelo script principal conforme a execução. Será preenchido em uma parte da função `estimate_voronoi_census_data()`. Vai conter um arquivo com toda a malha de polígonos, já com dados eleitorais e demográficos.

#### ./data/geo/voronois-merge

Trata-se de um diretório, de início vazio, que será populado com os arquivos gerados pelo script principal conforme a execução. Será preenchido em uma parte da função `make_voronoi_maps()`. Vai conter arquivos nos quais os diversos polígonos referentes a um mesmo local de votação já foram agrupados em um único objeto.

#### ./data/geo/voronois-pre-clip

Trata-se de um diretório, de início vazio, que será populado com os arquivos gerados pelo script principal conforme a execução. Será preenchido em uma parte da função `make_voronoi_maps()`. Vai conter arquivos com os polígonos de voronois antes de serem cortados no outline das cidades.

### ./data/geocode

O diretório é populado com o resultado da geolocalização, conforme o script é executado.

#### ./data/geocode/error-logs

De início vazio, o diretório deve ser preenchido com arquivos de texto contendo um log com locais de votação onde o processo de geolocalização falhou.


### ./data/locais

Contém os locais de votação necesséarios para gerar os diagramas, tanto em um formato por seção (urna) quando em formato já agregado por local de votação.


### .data/votos

Contém:

- A correspondência entre os códigos de cidade do IBGE e do TSE.

- `boletins-concatenados-2-turno.zip`, no subdiretório `boletim-urna`, contém, depois de descompactado, um arquivo com todos os arquivos .csv dos boletins de urna do 2º turno da eleição em uma única planilha. Para gerar um mapa do segundo turno, é necessário baixar e concatenar os arquivos .csv referentes ao primeiro turno no [Repositório de Dados Eleitorais do TSE](http://www.tse.jus.br/eleicoes/estatisticas/repositorio-de-dados-eleitorais-1/repositorio-de-dados-eleitorais).

