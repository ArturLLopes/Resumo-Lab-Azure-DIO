# Máquinas Virtuais Azure - Guia de Recursos e Dimensionamento


Este repositório contém informações essenciais sobre recursos e dimensionamento de máquinas virtuais (VMs) no Microsoft Azure. As VMs do Azure são recursos de computação escaláveis que permitem executar aplicações e cargas de trabalho na nuvem com diferentes capacidades de CPU, memória, armazenamento e rede.

## Tipos de VMs Disponíveis

### Série B (Burstable)
- **Uso**: Cargas de trabalho leves com picos ocasionais
- **Características**: Econômicas, ideais para desenvolvimento e testes

### Série D/Dv3/Dv4
- **Uso**: Propósito geral
- **Características**: Combinação equilibrada de CPU e memória

### Série E
- **Uso**: Aplicações com uso intensivo de memória
- **Características**: Otimizadas para bancos de dados e aplicações que requerem muita RAM

### Série F
- **Uso**: Computação intensiva
- **Características**: Otimizadas para CPU, processamento de dados

### Série L
- **Uso**: Aplicações com alta demanda de I/O
- **Características**: Armazenamento otimizado para alto IOPS

### Série N
- **Uso**: Inteligência artificial e visualização
- **Características**: Equipadas com GPU para IA, deep learning, jogos

### Série H
- **Uso**: Computação de alto desempenho (HPC)
- **Características**: Para simulações científicas e engenharia

## Componentes de Dimensionamento

### Recursos Principais
- **vCPU**: Núcleos virtuais responsáveis pelo processamento
- **RAM**: Memória para armazenar dados em uso
- **Disco**: SSDs ou HDDs para sistema e dados
- **Rede**: Largura de banda, IPs públicos/privados, grupos de segurança

### Redimensionamento
- Possível aumentar ou diminuir recursos conforme necessário
- Requer que a VM esteja desligada
- Dados são preservados durante o processo

## Recursos Avançados

### Alta Disponibilidade
- **Zonas de Disponibilidade**: VMs distribuídas em diferentes data centers
- **Conjuntos de Disponibilidade**: Distribuição entre racks físicos diferentes

### Escalabilidade
- **Scale Sets**: Escalamento automático de múltiplas instâncias
- **Discos Gerenciados**: Replicação, desempenho e segurança gerenciados pelo Azure

## Melhores Práticas

### Planejamento
- Utilize calculadoras de preços do Azure para dimensionamento adequado
- Considere a região da VM (custos e disponibilidade variam)
- Escolha tipos adequados à carga de trabalho

### Organização
- Use tags para organizar recursos
- Monitore custos regularmente
- Evite superdimensionamento para reduzir custos

### Otimização
- Avalie periodicamente se o dimensionamento ainda é adequado
- Considere usar VMs burstable para cargas variáveis
- Implemente monitoramento de performance

## Como Usar Este Guia

1. Identifique sua carga de trabalho
2. Escolha a série de VM apropriada
3. Dimensione os recursos necessários
4. Configure alta disponibilidade se necessário
5. Implemente monitoramento e otimização contínua

## Recursos Úteis

- [Calculadora de Preços do Azure](https://azure.microsoft.com/pricing/calculator/)
- [Documentação Oficial das VMs](https://docs.microsoft.com/azure/virtual-machines/)
- [Guia de Dimensionamento](https://docs.microsoft.com/azure/virtual-machines/sizes)

---

*Este guia serve como referência rápida para dimensionamento e escolha de VMs no Azure. Para informações detalhadas, consulte a documentação oficial da Microsoft.*