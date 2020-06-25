# Configuração inicial do Servidor de mapas Geoserver

[![Docker](https://img.shields.io/badge/docker-latest-green)](https://www.docker.com/)
[![GeoServer](https://img.shields.io/badge/geoserver-latest-green)](http://geoserver.org/)

Configuração inicial do servidor de mapas geoserver para a postagem de camadas a serem consumidas pelo [Sistema Web](https://github.com/ProjetoIntegradorADSFatec/web-gis) de visualização e identificação de Talhões proposto pelo projeto integrador

Aqui neste arquivo a prioridade e a estrutura de microsserviços, portanto vamos priorizar a instalação por meio da ferramenta de gerenciamento de container Docker.

# Montagem do ambiente de desenvolvimento

```
## Download da imagem
$ docker pull kartoza/geoserver

## execução do container Docker
$ docker run -d -p 8686:8080 --name geoserver -e STABLE_EXTENSIONS=charts-plugin,db2-plugin kartoza/geoserver
```

# Postagem das camadas

Verificar se o sistema encontra em execução no endereço [`localhost:8686/geoserver`](http://0.0.0.0:8686/geoserver/web/) e a página de administração do geoserver deverá ser exibida.

A credencial padrão do GeoServer é a seguinte:

  - *Usuário:* admin
  - *Senha:* geoserver

<p align = "center">
  <img width = "600px" src = "../../assets/geoserver-print.png">
</p>

Camadas necessárias para a execução:

- **[Postagem de camadas em Geotiff](https://docs.geoserver.org/stable/en/user/data/raster/geotiff.html)**: postagem das camadas das imagens de sensoriamento remoto do servidor FTP do INPE com os satélites Landsat e Sentinel-1;
- **[Postagem de Geometrias](https://www.google.com/url?q=https://docs.geoserver.org/stable/en/user/gettingstarted/shapefile-quickstart/index.html&sa=D&source=calendar&usd=2&usg=AOvVaw2oUDSmd3w1dZlnpITE-sHy)**: postagem das geometrias relacionadas a definição de talhões como resultado do sistema inteligente [PythonCNN](https://github.com/ProjetoIntegradorADSFatec/python-cnn).