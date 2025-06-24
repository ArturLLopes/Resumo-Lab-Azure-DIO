# Azure SLA e Alta Disponibilidade

> Guia prático para implementar alta disponibilidade em máquinas virtuais no Microsoft Azure

## 📋 Índice

- [SLAs de Máquinas Virtuais](#-slas-de-máquinas-virtuais)
- [Recursos de Alta Disponibilidade](#️-recursos-de-alta-disponibilidade)
- [Replicação de Armazenamento](#-replicação-de-armazenamento)
- [Implementação](#-implementação)
- [Guia de Decisão](#-guia-de-decisão)
- [Limitações](#️-limitações)
- [Calculadora de Downtime](#-calculadora-de-downtime)

## 🎯 SLAs de Máquinas Virtuais

| Configuração | SLA | Requisitos |
|--------------|-----|------------|
| VM única | **99,9%** | Disco Premium SSD obrigatório |
| Availability Set | **99,95%** | 2+ VMs, discos Premium |
| Availability Zones | **99,99%** | 2+ VMs em zonas diferentes |
| Disco padrão | **Sem SLA** | ❌ Não recomendado para produção |

## 🏗️ Recursos de Alta Disponibilidade

### Availability Set
```
Função: Distribui VMs entre domínios de falha e atualização
Configuração padrão: 2 fault domains, 5 update domains
Proteção: Falhas físicas e atualizações planejadas
SLA: 99,95%
```

### Availability Zones
```
Função: Zonas físicas isoladas na mesma região
Proteção: Falhas de datacenter completo
SLA: 99,99% (maior disponibilidade)
```

## 💾 Replicação de Armazenamento

| Tipo | Descrição | Caso de Uso |
|------|-----------|-------------|
| **LRS** | 3 cópias no mesmo datacenter | Menor custo |
| **ZRS** | Cópias em zonas diferentes | Alta disponibilidade |
| **GRS** | Replicação entre regiões | Recuperação de desastres |
| **RA-GRS** | GRS + acesso de leitura secundária | DR com leitura |

## ⚡ Implementação

### Pré-requisitos
- Conta Azure ativa
- Resource Group criado
- Região definida

### Criando Availability Set
```bash
# Via Azure Portal
1. Portal Azure → Availability Sets → + Create
2. Configure: nome, região, 2 fault domains, 5 update domains
3. Review + Create
```

### Criando VMs no Availability Set
```bash
# Via Azure Portal
1. Virtual Machines → + Create
2. Availability options → selecione o Availability Set
3. Configure disco Premium SSD
4. Repita para criar múltiplas VMs
```

### Verificação
```bash
# Verificar distribuição das VMs
1. Acesse o Availability Set
2. Confirme VMs em domínios diferentes
3. Exemplo: VM1 (FD0/UD0), VM2 (FD1/UD1)
```

## 🎯 Guia de Decisão

### Por Criticidade da Aplicação

| Cenário | Solução Recomendada | SLA Esperado |
|---------|-------------------|--------------|
| **Crítico** | Availability Zones + Premium SSD | 99,99% |
| **Importante** | Availability Set + Premium SSD | 99,95% |
| **Simples** | VM única + Premium SSD | 99,9% |
| **Dev/Test** | VM única + disco padrão | Sem SLA |

### Por Orçamento

| Orçamento | Configuração | Trade-off |
|-----------|-------------|-----------|
| **Alto** | Multi-zone | Máxima disponibilidade |
| **Médio** | Availability Set | Boa disponibilidade |
| **Baixo** | VM única Premium | Disponibilidade básica |

## ⚠️ Limitações

### ❌ Não é Possível
- Adicionar VM existente a Availability Set
- Mover VM entre Availability Sets
- Alterar zona de disponibilidade após criação

### ✅ Requisitos Obrigatórios
- Availability Set e VMs na mesma região
- Disco Premium SSD para garantir SLA
- Mesmo Resource Group
- Load Balancer para distribuir tráfego

## 📊 Calculadora de Downtime

| SLA | Downtime/Ano | Downtime/Mês |
|-----|-------------|-------------|
| 99,9% | ~8,7 horas | ~43 minutos |
| 99,95% | ~4,4 horas | ~22 minutos |
| 99,99% | ~52 minutos | ~4 minutos |

## 🔗 Links Úteis

- [Documentação Oficial Azure SLA](https://azure.microsoft.com/support/legal/sla/)
- [Azure Architecture Center](https://docs.microsoft.com/azure/architecture/)
- [Calculadora de Preços Azure](https://azure.microsoft.com/pricing/calculator/)

## 📝 Notas

- Este README foi criado com base nas especificações do Azure em 2025
- Sempre consulte a documentação oficial para informações atualizadas
- Teste as configurações em ambiente de desenvolvimento antes da produção

---

**Contribuições são bem-vindas!** 🚀