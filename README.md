<span id="topo">

<h1 align="center">Sprint 2: 20/09/2021 a 10/10/2021</h1>

<p align="center">
    <a href="#objetivos">Objetivos da sprint</a> &nbsp |&nbsp &nbsp
    <a href="#entregas">Entregas</a> &nbsp |&nbsp &nbsp
    <a href="#demo">Demonstração</a> &nbsp |&nbsp &nbsp 
    <a href="#metricas">Métricas do time</a> &nbsp |&nbsp &nbsp
    <a href="#links">Links úteis</a>
</p>

Nesta segunda sprint a equipe se atentou ao desejo do cliente pelo backend do site, responsável pelas consultas e processamento das imagens. Com o protótipo pronto e validado na última sprint, as tarefas se separaram entre refinar o frontend e massivamente aplicar esforços em pesquisas e testes de bibliotecas e tecnologias que atendessem aos requisitos, seguindo o backlog planejado para as sprints, visando entregar um projeto que permita a consulta aos repositórios a partir dos filtros aplicados, como cobertura de nuvens, área de interesse, período de tempo e satélite desejado.

<span id="objetivos">
    
## :dart: Objetivos da Sprint
Os requisitos (tanto do cliente como da instituição de ensino) abrangidos por essa sprint são:
- RF 01: Consulta às imagens definindo um ou mais satélites, área de interesse, período e cobertura de nuvens máxima;
- Requisito FATEC: aplicação do paradigma de programação orientada à objetos.

<span id="entregas">
        
## :heavy_check_mark: Entregas
    
### RF 01: Consulta às imagens definindo um ou mais satélites, área de interesse, período e cobertura de nuvens máxima
Tida como a funcionalidade principal do projeto, a consulta às imagens nos repositórios se deu com muita pesquisa e testes, desde conversas com o cliente, professores e profissionais de áreas semelhantes, até a criação de crawlers e uso de APIs de terceiros. O requisito se configura como a aplicação de consultas utilizando os filtros selecionados pelo portal web, sendo eles os satélites desejados, área de interesse, período e cobertura máxima de nuvens, sendo implementado utilizando Node.js e uma API externa chamada SAT-API, da Development Seed, que facilita o consumo das imagens dos satélites Landsat 8 e Sentinel 2 (confira a documentação completa [clicando aqui](./documentacao.pdf))
	
#### Envio dos filtros desejados
Na interface do site, há uma área destinada a capturar os filtros desejados para a busca das imagens e mandar tais dados para o backend, onde esta ação é de responsabilidade da classe "MapFilterProvider", que faz uma requisição para o backend com a resposta do formulário e captura o resultado, que depois é estruturado em forma de lista de imagens que correspondiam às escolhas aplicadas, dando a possibilidade de visualização no mapa ou de download (funcionalidade que será desenvolvida na próxima sprint), mas no caso de erro nessa requisição a exceção é capturada e exibida no terminal.
	
#### Realização da busca e resposta ao site (integração)
A API foi usada através do Axios e da criação de uma classe “SatSearchController”, que contém o método "index" que recebe dois parâmetros: req, do tipo Request, e res, do tipo Response, onde em seu corpo há um bloco de “try catch” para obtenção das imagens ou o tratamento de alguma exceção ou erro. No bloco “try” há o recebimento dos filtros via corpo da requisição do frontend e um vetor para armazenamento das imagens que seriam obtidas como resposta, sendo aplicado um laço de repetição para cada satélite escolhido entre as opções possíveis, criando duas variáveis: “inputBody”  (estrutura as informações para a busca na API externa) e “headers” (cabeçalho da requisição à API). Com isso é criada a constante “satCollection” que espera o resultado do método “POST” aplicado na API, passando como argumentos o caminho da busca e as variáveis "inputBody" e "headers”, armazenando e enviando como resposta ao frontend o vetor “imagesResponse” como JSON. Já na situação onde a operação não for bem sucedida, o bloco de “catch” captura o erro e o exibe no console.
	
→ [Voltar ao topo](#topo)
	
<span id="demo">
	
## 🖥️ Demonstração
<p align="center"><img src="./demo-sprint-2.gif" /></p>
	
### Tecnologias escolhidas
Para os objetivos desenvolvidos na segunda sprint foram utizadas as seguintes tecnologias:

- **React.js:** usada para a criação de interfaces gráficas com a sintaxe JSX;
- **TypeScript:** usada para aplicação de conceitos do paradigma da Programação Orientada a Objetos;
- **Leaflet:** usada para construir a interface do mapa;
- **STAC-API:** permite consultar imagens dos satélites Landsat 8 e Sentinel 2 (API disponibilizada pela Development Seed).

→ [Voltar ao topo](#topo)

<span id="metricas">
    
## :chart_with_upwards_trend: Métricas do time
Em prol de um melhor aproveitamento das habilidades de cada integrante, o time foi separado em duas frentes: frontend e backend, onde o time front ficou responsável pela conversão dos componentes funcionais em classes e pesquisas sobre integração front-back e possibilidades de visualização das imagens no mapa, já o time back focou em pesquisas e testes com as tecnologias sugeridas pela empresa para o consumo das imagens nos repositórios em nuvem. O acompanhamento de atividades, de responsabilidade da Scrum Master, se encontra na imagem adiante, que contém o gráfico Burndown gerado pela equipe (onde o eixo X são os dias trabalhados na sprint e os valores do eixo Y representam as entregas e esforços realizados com o passar do tempo), incluindo as atividades desenvolvidas e seus responsáveis.
    
<p align="center"><img src="./burndown.png" /></p>
    
→ [Voltar ao topo](#topo)
    
<span id="links">
    
## :link: Links úteis
- Documentação em PDF, estilo monografia (requisito não funcional do projeto): [clique aqui](./documentacao.pdf)
- Repositórios de códigos: [Portal Web](https://github.com/Equipe-Polaris-DSM-2021/web), [API](https://github.com/Equipe-Polaris-DSM-2021/api)
- Tags geradas em cada repositório que simbolizam o fim da 2ª sprint: [API](https://github.com/Equipe-Polaris-DSM-2021/api/releases/tag/sprint-02), [Portal Web](https://github.com/Equipe-Polaris-DSM-2021/web/releases/tag/sprint-02)
