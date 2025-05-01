Construa sistemas Multi-Agents com YAML | Integração com Tools | Deploy no CrewAI Enterprise | Projetos completos

📋 Descrição

Este repositório apresenta uma coleção de projetos completos para construir sistemas multi-agents utilizando o formato YAML, integrar agentes com Tools e realizar o deploy na plataforma CrewAI Enterprise. Cada exemplo inclui configuração detalhada, exemplos de uso e instruções de deployment.

✨ Funcionalidades

Definição de agentes e fluxos de trabalho via YAML

Integração com ferramentas externas (APIs, bases de dados, serviços internos)

Orquestração de múltiplos agentes para soluções complexas

Scripts e pipelines de deploy no CrewAI Enterprise

Exemplos práticos e templates reutilizáveis

📂 Estrutura do Projeto

├── agents/             # Arquivos YAML definindo os agentes
│   ├── agente-1.yml
│   ├── agente-2.yml
│   └── ...
├── tools/              # Implementações das Tools em Python/JS/etc.
│   ├── tool_api.py
│   ├── tool_database.py
│   └── ...
├── deploy/             # Scripts e configurações de deployment
│   ├── crewai-config.yml
│   ├── deploy.sh
│   └── ...
├── examples/           # Exemplos de uso para cada projeto
│   ├── example_1.md
│   └── ...
├── docs/               # Documentação adicional e diagramas
├── .gitignore
└── README.md           # Este arquivo

⚙️ Pré-requisitos

Python 3.8+ ou Node.js 14+ (dependendo das Tools)

CrewAI Enterprise: acesso e credenciais configuradas

Ferramenta de linha de comando do CrewAI instalada (CLI)

🛠️ Instalação e Configuração

Clone este repositório:

git clone https://github.com/seu-usuario/seu-repo.git
cd seu-repo

Crie e ative um ambiente (opcional para Python):

python -m venv .venv
source .venv/bin/activate  # ou Activate.ps1 no Windows

Instale dependências (exemplo em Python):

pip install -r requirements.txt

Configure credenciais do CrewAI:

export CREWAI_API_KEY="seu_token_aqui"

📑 Definição de Agentes (YAML)

Cada agente é configurado em um arquivo YAML dentro de agents/. Exemplo básico:

agent:
  name: processador-dados
  description: "Coleta e processa dados de entrada"
  tools:
    - name: api_service
      input: { endpoint: "/v1/dados", method: "GET" }
  steps:
    - call: api_service
    - run: filtrar_resultados

A sintaxe e os parâmetros disponíveis estão documentados em docs/agents.md.

🔌 Integração com Tools

As Tools são implementações de funções ou classes que podem ser chamadas pelos agentes. Exemplo em Python:

class ApiService:
    def __init__(self, endpoint: str):
        self.endpoint = endpoint

    def run(self, payload: dict) -> dict:
        response = requests.get(self.endpoint, params=payload)
        return response.json()

Registre cada Tool no arquivo tools/index.py para que os agentes consigam resolver pelo nome.

🚀 Deploy no CrewAI Enterprise

Gere o pacote de deployment:

crewai package --config deploy/crewai-config.yml

Envie para a plataforma:

crewai deploy --package ./dist/agents.pkg

Monitore status:

crewai status --deployment-id <ID_RETORNADO>

Detalhes de configuração e referências de CLI estão em docs/deploy.md.

📚 Exemplos de Uso

Confira a pasta examples/ para guias passo a passo:

example_1.md: Projeto de ingestão de dados multi-agent

example_2.md: Orquestração de análise de texto com Agents+Tools

🤝 Contribuição

Contribuições são bem-vindas! Abra Issues ou PRs seguindo o guia em docs/CONTRIBUTING.md.

📄 Licença

Este projeto está licenciado sob a MIT License. Veja o arquivo LICENSE para mais detalhes.

