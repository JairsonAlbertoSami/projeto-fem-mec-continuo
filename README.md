# Projeto FEM-MEC-Contínuo: DeepONet & Upscaling

Este repositório contém o trabalho de conclusão desenvolvido como requisito avaliativo conjunto para as disciplinas de **Elementos Finitos (FEM)** e **Mecânica do Contínuo**.

## Objetivo do Trabalho

O projeto propõe uma abordagem híbrida para resolver problemas de fluxo em meios porosos. A metodologia consiste em:

1.  **Simulação Numérica (FEM):** Simulação de permeabilidade de forma **anisotrópica** para resolução do problema de **Darcy**, com o objetivo de determinar a **permeabilidade efetiva**.
2.  **Aprendizado de Máquina (DeepONet):** Utilização dos dados gerados pelas simulações FEM para treinar uma rede neural do tipo **DeepONet**. O objetivo da rede é realizar a predição da **permeabilidade efetiva** em duas direções principais, atuando como um substituto computacionalmente eficiente (*surrogate model*) para o solver clássico.

## Estrutura do Repositório


```
PROJETO-FEM-MEC-CONTINUO/
	dataset_deeponet/
		data_independente/
	modelo_deeponet/
		modelo_deepONet.pth
		modelo_deeponet_permeabilidade.pth
	notebooks/
		deepONet.ipynb
		FEM_upscaling.ipynb
	results/
		plots/
			comparacao_performance_baseline.png
			evolucao_mse_treino_validacao.png
			histograma_residuos_deeponet.png
			regressao_predito_vs_real_Kxx_Kyy.png
	src/
		.gitignore
		LICENSE
		README.md
	requirements.txt
```

## Como Reproduzir os Resultados

Siga os passos abaixo para configurar o ambiente de desenvolvimento e executar as simulações.

### Pré-requisitos

- Git instalado
- Python 3.8+
- Gerenciador de pacotes (pip ou conda)

### 1. Clonar o Repositório

```bash
git clone https://github.com/JairsonAlbertoSami/projeto-fem-mec-continuo.git
cd PROJETO-FEM-MEC-CONTINUO
```

### 2. Configurar o Ambiente Virtual

Recomenda-se usar um ambiente virtual para evitar conflitos de versões.

**Opção A: conda (recomendado)**

```bash
# 1. Criar o ambiente
conda create -n deeponet_env python=3.8

# 2. Ativar o ambiente
conda activate deeponet_env

```

**Opção B: venv (padrão do Python)**

```bash
# 1. Criar o ambiente virtual
python -m venv venv

# 2. Ativar o ambiente
# Windows
.\venv\Scripts\activate
# Linux ou macOS
source venv/bin/activate

# 3. Instalar dependências
pip install -r requirements.txt
```

### 3. Executar os Notebooks

Com o ambiente ativado e as dependências instaladas, inicie o servidor Jupyter:

```bash
jupyter notebook
```

No navegador, acesse a pasta `notebooks/` e execute na sequência sugerida:

1. `deepONet.ipynb`: treinar o modelo ou carregar pesos pré-treinados e avaliar a rede.
2. `FEM_upscaling.ipynb`: comparar os resultados da rede com o método tradicional de Elementos Finitos (FEM).

### Resultados Esperados

Ao executar os notebooks, os gráficos de performance e comparação são salvos automaticamente em `results/plots`. O modelo deve reproduzir os gráficos de convergência do MSE e os histogramas de resíduos presentes nessa pasta.

### Licença

Este projeto está licenciado sob a Licença MIT - consulte o arquivo `LICENSE` para mais detalhes.
