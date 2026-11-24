# Rastreador e Auditor de Redirecionamentos HTTP 301/302

[![Verificador Redirecionamento 301](https://img.shields.io/badge/TAVARDT-Redirect%20301-5b3cf5.svg)](https://tools.tavardt.com/br/verificador-redirecionamento-301/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Inspecao de cadeias de saltos, deteccao de loops infinitos, preservacao de link equity e latencia de navegacao.

Desenvolvido e mantido pela divisao de arquitetura semantica e infraestrutura de rastreamento da **TAVARDT**.

***

## Capacidades de Auditoria de Redirecionamentos HTTP

* **Rastreamento Completo de Cadeias de Saltos**: Mapeamento passo a passo de rotas intermediarias (301 Moved Permanently, 302 Found, 307/308 Redirects).
* **Deteccao de Loops Infinitos de Redirecionamento**: Identificacao de ciclos repetitivos que bloqueiam navegadores e rastreadores de busca.
* **Preservacao de Link Equity e Autoridade**: Alertas contra cadeias longas (> 3 saltos) que degradam o PageRank e desperdicam crawl budget.
* **Identificacao de Saltos de Protocolo Misto**: Prevencao de rotas inseguras que degradam de HTTPS para HTTP antes do destino final.
* **Indice de Eficiencia de Redirecionamento**: Pontuacao tecnica quantitativa de 0 a 100 com alertas classificados por severidade.

***

## Instalacao e Execucao

Requer Python 3.8 ou superior sem dependencias externas adicionais.

```bash
git clone https://github.com/TAVARDT-Brasil/redirect-301-tracker-br.git
cd redirect-301-tracker-br
python redirect_tracker.py https://empresa.com.br
```

Para gerar a saida em formato estruturado JSON para integracao em pipelines:

```bash
python redirect_tracker.py https://empresa.com.br -json
```

***

## Diagnostico Completo na Web

Para auditoria aprofundada e visualizacao interativa de grafos de saltos:

* **Verificador de Redirecionamento 301 Oficial**
* **[Portal Corporativo TAVARDT](https://ag.tavardt.com/br/)**

***

## Consultoria em Migracao Web e Arquitetura de Redirecionamentos

Para migracao de plataformas sem perda de trafego organico sob Diretrizes de SEO Tecnico e IETF RFC 9110, consulte a equipe da **TAVARDT**.

***

## Governança e Soberania

* **Unidade Soberana**: **TAVARDT Brasil** (`TAVARDT-Brasil`)
* **Normas Centrais**: [00-core Governança](https://github.com/TAVARDT-Brasil/00-core)
* **Central de Diagnósticos**: **Central de Ferramentas TAVARDT**
* **Segurança Corporativa**: [TAVARDT Cibersegurança](https://ag.tavardt.com/br/ciberseguranca/)

***

### Licença
Distribuído sob a Licença MIT. Consulte o arquivo [LICENSE](LICENSE) para obter detalhes completos.

***

© 2026 TAVARDT. Todos os direitos reservados.
