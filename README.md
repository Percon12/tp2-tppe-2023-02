# Boas Práticas de Código e Refatoração

## Integrantes do grupo

| Nome | Matrícula |
| -- | -- |
| Eurico Menezes de Abreu Neto | 200017519 |
| Felipe Correia Andrade | 180113259 |
| Mateus Brandão Teixeira | 180127535 |

## Introdução

O desenvolvimento de software envolve não apenas a criação de código funcional, mas também a adoção de práticas que visam melhorar a legibilidade, manutenibilidade e eficiência do código. Neste contexto, as boas práticas de código e técnicas de refatoração desempenham um papel crucial.

Este documento explora cinco boas práticas essenciais para o desenvolvimento de código de qualidade, ilustrando cada uma com exemplos práticos e demonstrando como a refatoração pode ser aplicada para aprimorar o código existente.

## 1. Simplicidade

### O que é?
A simplicidade no código refere-se à minimização da complexidade desnecessária. Um código simples é mais fácil de entender, manter e modificar. A simplicidade é alcançada através da eliminação de detalhes desnecessários e da quebra de problemas complexos em partes menores e mais compreensíveis.

### Por que é importante?
Código complexo pode levar a erros, dificuldades de manutenção e compreensão limitada. A simplicidade, por outro lado, promove uma estrutura mais clara e facilita a colaboração entre desenvolvedores.

### Exemplo:
```python
# Código Inicial
def calcular_resultado_complexo(dados):
    # lógica complicada aqui
    resultado = 0
    for item in dados:
        resultado += item["valor"] * item["peso"]
    return resultado

# Refatoração (Extrair Método)
def calcular_resultado_simples(dados):
    resultado = 0
    for item in dados:
        resultado += calcular_peso_valor(item)
    return resultado

def calcular_peso_valor(item):
    return item["valor"] * item["peso"]
```

**Explicação Adicional:**
A refatoração "Extrair Método" simplifica o código ao dividir a lógica complexa em partes menores e mais compreensíveis.

## 2. Modularidade

### O que é?
A modularidade envolve a divisão do sistema em módulos independentes e bem definidos, com baixo acoplamento e alta coesão. Cada módulo deve executar uma função específica e ser intercambiável, promovendo a reutilização e manutenção eficientes.

### Por que é importante?
Módulos bem definidos facilitam a compreensão do sistema, reduzem dependências indesejadas e promovem a escalabilidade do software.

### Exemplo:
```python
# Código Inicial
class SistemaMonetario:
    def calcular_taxa_juros(self, valor):
        # lógica para calcular a taxa de juros
        return valor * 0.1

    def processar_transacao(self, valor):
        # lógica para processar transação
        taxa = self.calcular_taxa_juros(valor)
        # mais lógica de processamento
        return resultado

# Refatoração (Extrair Módulo)
class TaxaJuros:
    def calcular_taxa(self, valor):
        return valor * 0.1

class SistemaMonetario:
    def __init__(self):
        self.taxa_juros = TaxaJuros()

    def processar_transacao(self, valor):
        taxa = self.taxa_juros.calcular_taxa(valor)
        # mais lógica de processamento
        return resultado
```

**Explicação Adicional:**
A refatoração "Extrair Módulo" melhora a modularidade, separando a lógica de cálculo de taxa em um módulo independente.

## 3. Boas Interfaces

### O que é?
Boas interfaces definem contratos claros e intuitivos para módulos, classes e funções. Uma boa interface simplifica a interação entre diferentes partes do sistema, reduzindo a complexidade e facilitando o uso correto das funcionalidades.

### Por que é importante?
Interfaces bem projetadas promovem a comunicação eficaz entre componentes, facilitando a manutenção e evitando erros de integração.

### Exemplo:
```python
# Código Inicial
class ProcessadorPagamento:
    def processar_pagamento(self, valor, metodo, informacoes_adicionais):
        # lógica de processamento
        return resultado

# Refatoração (Extrair Interface)
class PagamentoInterface:
    def processar_pagamento(self, valor):
        pass

class ProcessadorPagamento(PagamentoInterface):
    def processar_pagamento(self, valor):
        # lógica de processamento
        return resultado
```

**Explicação Adicional:**
A refatoração "Extrair Interface" define uma interface clara para processamento de pagamento, facilitando o entendimento e uso adequado.

## 4. Ausência de Duplicidades

### O que é?
A ausência de duplicidades refere-se à eliminação de código redundante. A reutilização de código através da eliminação de duplicidades simplifica a manutenção e reduz a probabilidade de inconsistências.

### Por que é importante?
Código duplicado pode levar a erros difíceis de rastrear e dificulta a atualização consistente do sistema.

### Exemplo:
```python
# Código Inicial
def calcular_area_circulo(raio):
    return 3.14 * raio * raio

def calcular_volume_esfera(raio):
    return (4 / 3) * 3.14 * raio * raio * raio

# Refatoração (Extrair Método)
def calcular_area_circulo(raio):
    return math.pi * raio * raio

def calcular_volume_esfera(raio):
    return (4 / 3) * math.pi * raio * raio * raio
```

**Explicação Adicional:**
A refatoração "Extrair Método" reduz duplicidades, substituindo a constante π e melhorando a precisão do cálculo.

## 5. Boa Documentação

### O que é?
Boa documentação fornece informações claras e úteis sobre o propósito, funcionamento e uso do código. Uma boa documentação simplifica a compreensão e manutenção do sistema.

### Por que é importante?
A documentação adequada auxilia desenvolvedores no entendimento do código, facilita a colaboração e promove uma manutenção eficiente.

### Exemplo:
```python
# Código Inicial
def calcular_resultado(dados):
    # lógica para calcular o resultado
    resultado = 0
    for item in dados:
        resultado += item["valor"] * item["peso"]
    return resultado

# Refatoração (Extrair Método)
def calcular_resultado(dados):
    # lógica para calcular o resultado
    resultado = 0
    for item in dados:
        resultado += calcular_peso_valor(item)
    return resultado

def calcular_peso_valor(item):
    # lógica para calcular peso vezes valor
    return item["valor"] * item["peso"]
```

**Explicação Adicional:**
A refatoração "Extrair Método" torna o código mais autodescritivo, reduzindo a necessidade de comentários desnecessários.

---

Este guia destaca a importância de cinco boas práticas de código, oferece exemplos práticos e demonstra como aplicar refatorações específicas para melhorar a qualidade do código. Adapte esses princípios ao seu contexto e promova um ambiente de desenvolvimento de software mais eficiente e colaborativo.
