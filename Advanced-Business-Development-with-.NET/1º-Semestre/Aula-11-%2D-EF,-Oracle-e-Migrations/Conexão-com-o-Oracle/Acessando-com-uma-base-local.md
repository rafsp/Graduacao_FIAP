[[_TOC_]]

# Vídeo explicativo
::: video
<iframe width="1088" height="612" src="https://www.youtube.com/embed/fOsp_IRoWTc" title="Oracle: Trabalhe com Oracle gratuitamente na sua máquina local" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
:::

# Sobre a imagem
https://hub.docker.com/r/gvenzl/oracle-free

# Comado docker para gerar uma base Oracle na máquina local
```bash
docker run -d -p 1521:1521 -e ORACLE_PASSWORD=dOJN@IhD12342 --name oracle-free gvenzl/oracle-free
```

# Comando log para verificar os logs do processo
```bash
docker logs oracle-free -f
```

# Acessando no SQL Developer