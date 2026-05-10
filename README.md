# Dashboard SEDLAC: Indicadores de Pobreza e Desigualdade na América Latina e Caribe

Neste projeto, desenvolvemos um dashboard interativo, construído a partir de dados do SEDLAC -
Socio-Economic Database for Latin America and the Caribbean (CEDLAS e The World Bank), 
cobrindo indicadores de pobreza e desigualdade de renda para países da América Latina e Caribe
desde os anos 1980 até as últimas fontes disponibilizadas pelas instituições nacionais.

## Dashboard

🔗 [Visualizar no Tableau Public](https://public.tableau.com/views/DashboardSEDLAC/VisoGeral?:language=pt-BR&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

---

## Estrutura do repositório
```
dashboard-sedlac/
├── parser.py                           # Pipeline de parsing e tratamento dos dados
├── DashboardSEDLAC.twbx                # Arquivo fonte do Tableau Public
│
└── data/
    ├── raw/                            # Arquivos originais do SEDLAC
    │   ├── 2024_Act1_poverty_LAC.xlsx
    │   └── 2025_Act1_inequality_LAC.xlsx
    │
    └── parsed/                         # Dados tratados prontos para o Tableau
        ├── sedlac_indicators.csv       # Indicadores nacionais em formato longo
        ├── sedlac_deciles.csv          # Participação dos decis de renda
        └── sedlac_regional.csv         # Headcount de pobreza por sub-região
```
---

## Abas do dashboard

### 1. Visão Geral
Panorama nacional de indicadores de pobreza e desigualdade de renda para países da América Latina e Caribe:
- Evolução temporal por país (por indicador selecionado)
- Mapa coroplético por indicador e ano selecionados
- Ranking Top-10 países por indicador e ano selecionados

**Indicadores disponíveis:** Índice de Gini, T de Theil, Coeficiente de Variação (CV),
Índices de Atkinson A(1) e A(2), Divergência Logarítmica E(0), Índice de Wolfson, Gini urbano/rural, 
Headcount de pobreza (USD 2.15 / 3.65 / 6.85), Pobreza Multidimensional em áreas urbanas (NBI)

### 2. Visão Local
Panorama, a nível regional, de indicadores unidimensionais de pobreza:
- Headcount de pobreza (USD 2.15 / 3.65 / 6.85) por região dentro de cada país
- Evolução temporal, por região, do indicador selecionado
- Heatmap comparativo, do indicador escolhido, entre dois períodos
- Scatterplot: headcount nacional × headcount da região mais pobre

**Indicadores disponíveis:** Headcount de pobreza (USD 2,15 / 3,65 / 6,85) por sub-região

### 3. Desigualdade
Panorama evolutivo da distribuição de renda per capita, a nível nacional, por decis:
- Participação dos decis por país, segundo o ano escolhido
- Evolução da participação de D1 a D10, por país escolhido
- Razões de desigualdade: Palma, Q1/Q5, Top20/Bottom40, D1/D10

---

## Pipeline de dados

Os dados brutos do SEDLAC estão em formato hierárquico (Excel com múltiplas 
abas e cabeçalhos mesclados). O script `parser.py` realiza:

1. **Parsing** das abas relevantes de pobreza e desigualdade
2. **Normalização** para formato longo (*tidy data*)
3. **Geração** de três CSVs temáticos para o Tableau

### Execução

```bash
# Instalar dependências
pip install pandas openpyxl

# Executar o parser
python parser.py
```

Este código busca os arquivos de entrada em `data/raw/`, enquanto os arquivos
gerados serão salvos em `data/parsed/`, para facilitar a identificação posterior.

---

## Fonte dos dados

> **SEDLAC (CEDLAS e The World Bank)**. Socio-Economic Database for Latin America and the Caribbean  
> Disponível em <https://www.cedlas.econo.unlp.edu.ar/wp/en/estadisticas/sedlac/estadisticas/>
> Consultado em: maio de 2026

Os dados não são estimativas oficiais dos países ou do Banco Mundial.  
Citação recomendada: *"Source: SEDLAC (CEDLAS and The World Bank)"*

---

## Uso de inteligência artificial generativa

O código Python para parsing dos dados (`parser.py`) foi desenvolvido com o suporte de inteligência artificial generativa (GenAI). A ferramenta utilizada foi:

> ANTHROPIC. **Claude Sonnet 4.6**. San Francisco: Anthropic, 2026. Disponível em: https://claude.ai. Acesso em: 10 mai. 2026.

O uso de IA não substitui a responsabilidade intelectual do autor sobre as escolhas metodológicas, interpretações e resultados apresentados.

---

## Tecnologias

- **Python**: parsing e tratamento dos dados (`pandas`, `openpyxl`)
- **Tableau Public**: visualização e publicação

---

## Licença

Código disponibilizado sob licença MIT.  
Os dados originais seguem os termos de uso do SEDLAC/CEDLAS.
