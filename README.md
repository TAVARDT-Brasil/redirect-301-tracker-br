# Rastreador de Redirecionamentos HTTP 301 e Cadeias de Saltos

[![Verificador Redirecionamento 301](https://img.shields.io/badge/TAVARDT-Redirect%20301-5b3cf5.svg)](https://tools.tavardt.com/br/verificador-redirecionamento-301/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Auditoria de rotas de redirecionamento, deteccao de loops infinitos, conservacao de autoridade e orcamento de rastreamento.

Desenvolvido e mantido pela divisao de engenharia de indexacao e auditoria de infraestrutura de busca da **TAVARDT**.

***

## Vetores de Risco e Impacto Operacional em Redirecionamentos HTTP

Cadeias excessivas de redirecionamento diluem a autoridade organica de PageRank, aumentam a latencia de carregamento e esgotam o orcamento de rastreamento no Brasil. Rotas circulares causam travamento nos navegadores e levam ao descarte imediato da pagina pelos buscadores.

O downgrade de protocolo de HTTPS para HTTP durante os saltos expoe dados a interceptacao e provoca alertas de seguranca aos visitantes. A auditoria sistematica garante que migracoes de dominio preservem o trafego sem gerar gargalos tecnicos.

***

## Capacidades Centrais de Auditoria Tecnica

* **Rastreamento Salto a Salto Controlado**: Inspecao detalhada de codigos 301, 302, 303, 307 e 308 sem seguir redirecionamentos cegamente.
* **Deteccao Instantanea de Loops Infinitos**: Identificacao de rotas circulares via conjunto de URLs visitadas, abortando a execucao e zerando a pontuacao.
* **Validacao de Status do Destino Final**: Inspecao do codigo HTTP final da rota, deduzindo 60 pontos caso a resposta seja diferente de 200 OK.
* **Controle de Extensao e Link Equity**: Penalizacao de cadeias longas com deducao de 15 pontos por salto extra acima de 3 etapas para preservar autoridade.
* **Auditoria de Downgrade Inseguro**: Identificacao de transicoes de HTTPS seguro para HTTP desprotegido com penalidade automatica de 20 pontos.
* **Afericao de Latencia Cumulativa**: Registro de duracao individual por salto e tempo acumulado da cadeia em milissegundos via contadores de precisao.
* **Indice de Eficiencia de Redirecionamento**: Pontuacao tecnica de 0 a 100 categorizando o caminho em OPTIMISED, LONG CHAIN (WARNING) ou FAILURE / LOOP (CRITICAL).

***

## Instalacao e Execucao

Requer Python 3.8 ou superior sem dependencias externas adicionais.

```bash
git clone https://github.com/TAVARDT-Brasil/redirect-301-tracker-br.git
cd redirect-301-tracker-br
python redirect_tracker.py https://empresa.com.br
```

Para gerar a saida em formato estruturado JSON em esteiras de integracao continua:

```bash
python redirect_tracker.py https://empresa.com.br -j
```

***

## Perguntas Frequentes (FAQ Tecnico)

### 1. Como cadeias longas de redirecionamento afetam a transmissao de autoridade?
Cada salto adicional em uma cadeia dissipa uma fracao da autoridade acumulada e retarda a indexacao pelo Googlebot. Quando a rota ultrapassa tres saltos, os motores de busca podem interromper o rastreamento antes de atingir o destino final.

### 2. De que forma o utilitario intercepta loops de redirecionamento infinito sem travar?
O script armazena cada URL visitada em uma estrutura de dados de controle e utiliza um manipulador que impede redirecionamentos automaticos. Se uma rota circular for detectada, o processo e abortado imediatamente e a nota tecnica e zerada.

### 3. Qual o impacto de um downgrade de protocolo de HTTPS para HTTP durante a cadeia?
O transito intermediario por HTTP nao criptografado anula as garantias de seguranca da conexao e expoe os dados a interceptacao na rede. Essa falha de configuracao acarreta deducoes de pontuacao e ativa alertas de seguranca nos navegadores.

### 4. Qual a diferenca tecnica entre redirecionamentos permanentes e temporarios?
Os codigos 301 e 308 consolidam o indice e transferem a autoridade historica para o novo endereco de forma definitiva. Ja os codigos 302 e 307 indicam estados provisorios, instruindo os buscadores a manterem a URL original nos resultados.

### 5. Por que e fundamental auditar a resposta HTTP do destino final de cada rota?
Uma cadeia que culmina em codigos de erro 4xx ou 5xx quebra a navegacao e descarta os beneficios de migracao de links. O validador testa a resposta final em tempo real para certificar a entrega bem-sucedida do status 200 OK.

***

## Consultoria em SEO Tecnico e Migracao de Sites

Para projetos complexos de migracao de dominio e conformidade com diretrizes do W3C, consulte a equipe da **TAVARDT**.

***

## Links Uteis

* **Portal Corporativo:** https://ag.tavardt.com/br/
* **Suite de Diagnosticos:** https://tools.tavardt.com/br/
* **Contato Tecnico:** https://ag.tavardt.com/br/contato/

***

### Licenca
Distribuido sob a Licenca MIT. Consulte o arquivo LICENSE para termos completos.

***

© 2026 TAVARDT. Todos os direitos reservados.
