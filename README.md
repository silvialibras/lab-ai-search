# 
# **🔍 Repositório: Azure Cognitive Search - AI Search para indexação e consulta de dados

## **📌 Visão Geral**
Documentação detalhada do processo de implementação de uma solução de mineração de conhecimento para avaliações de clientes da Fourth Coffee.

## **🛠️ Passo a Passo Implementado**

### **1. Criação dos Recursos Azure**
| Recurso | Nome | Configurações |
|---------|------|--------------|
| **Azure AI Search** | azureaisearchmod04 | Local: East US 2, Camada: Básico |
| **Cognitive Services** | (Vinculado ao AI Search) | Standard S0, mesma região |
| **Storage Account** | stoaimod4dio | LRS, acesso anônimo habilitado |

### **2. Configuração Detalhada**

#### **📦 Preparação do Storage Account**
1. Criado container `coffee-reviews` com acesso público
2. Upload dos arquivos de avaliação (disponíveis em [aka.ms/mslearn-coffee-reviews](https://aka.ms/mslearn-coffee-reviews))
3. Configuração de acesso anônimo habilitada

#### **🔍 Configuração do Azure AI Search**
1. Assistente de **Importação de Dados** acionado
2. Fonte de dados: `coffee-customer-data` (Blob Storage)
3. Modo de análise: Padrão

#### **🧠 Habilidades Cognitivas**

{
  "skillset": "coffee-skillset",
  "skills": [
    {
      "skill": "Extração de Localizações",
      "source": "/document/merged_content"
    },
    {
      "skill": "Análise de Sentimento",
      "inputs": ["/document/content"]
    }
  ]
}


### **3. Processo de Indexação**
1. **Index criado**: `coffee-index`
   - Chave: `metadata_storage_path`
   - Campos indexados: conteúdo, localizações, sentimento, imagem.

2. **Indexador configurado**: `coffee-indexer`
   - Agendamento: Uma vez
   - Habilitação de Base-64 encoding

3. **Knowledge Store**:
   - Container: `knowledge-store` (privado)
   - Projeções habilitadas: Documentos, Páginas, Frases-chave.

## **🔍 Consultas Realizadas**

### **1. Busca Geral**

{
  "search": "*",
  "count": true
}

**Resultado**: 5 documentos indexados

### **2. Filtro por Localização (Chicago)**

{
  "search": "locations:'Chicago'",
  "count": true
}

**Resultado**: 3 documentos

### **3. Filtro por Sentimento Negativo**

{
  "search": "sentiment:'negative'",
  "count": true
}

**Resultado**: 1 documento

## **📊 Análise do Knowledge Store**
1. **Estrutura Criada**:
   - Blob container com metadados por documento
   - Tabelas relacionais para frases-chave e entidades

2. **Insights Obtidos**:
   - Imagens processadas e armazenadas em `coffee-skillset-image-projection`
   - JSONs completos com todos os metadados em `objectprojection.json`

## **✅ Validações Realizadas**
1. Verificação do status do indexador (sucesso)
2. Confirmação de documentos no container `knowledge-store`
3. Teste de consultas no Search Explorer

## **📌 Lições Aprendidas**
1. ** Implementação de recursos
2. ** criação de container
3. **Importância do OCR** para documentos escaneados
4. **Configuração de granularidade** como páginas melhora resultados
5. **Knowledge Store** permite análises adicionais

## **🚀 Próximos Passos**
1. Integração com Power BI
2. Configuração de alertas para menções negativas
3. Expansão para outros tipos de documentos


# **💼 Valor de Negócio dos Recursos Azure que podem ser implementados**

## **🚀 Impacto Estratégico nos Negócios**
### **1. Azure AI Search - O Poder da Busca Inteligente**
**Para Gestores:**
- Redução de **80% do tempo** para encontrar informações críticas em documentos
- Capacidade de **descobrir insights ocultos** em milhares de páginas em segundos
- **Vantagem competitiva**: Tomada de decisão baseada em dados estruturados automaticamente

### **2. Azure Storage Account - Mais que Armazenamento**
**Para Operações:**
- **Redução de 60% nos custos** com armazenamento físico e gerenciamento de documentos
- **Acesso seguro** de qualquer lugar, com controle granular de permissões
- **Integração nativa** com outros serviços Azure (AI, Analytics)

**Caso Real:**  
Uma rede de farmácias reduziu o processamento de recibos médicos de **48 horas para 15 minutos** com upload automático para Blob Storage.

### **3. Cognitive Services - Inteligência Aplicada**
**Para Atendimento ao Cliente:**
- **Análise automática de sentimentos** em avaliações (NPS, reclamações)
- **Detecção proativa** de crises (picos em menções negativas)
- **Automatização de categorização** de solicitações (ex: "reclamação sobre entrega")

**Métrica Importante:**  
Empresa de e-commerce aumentou **30% na satisfação do cliente** ao identificar e resolver padrões de reclamações automaticamente.

## **💡 Aplicações por Área**
### **Jurídico**
- **Busca semântica** em contratos ("cláusula de confidencialidade")
- **Alertas automáticos** para vencimentos de contratos

### **Varejo**
- **Agrupamento automático** de reclamações por produto/loja
- **Detecção de tendências** em avaliações de produtos

## **📌 Por Que Investir Nessa Solução?**
1. **ROI Comprovado**: Payback em <6 meses para 72% das implementações
2. **Escalabilidade Ilimitada**: Processa 100 ou 10 milhões de documentos com a mesma eficiência
3. **Integração com Ecossistema Microsoft**: Power BI, Teams, SharePoint

## **🔮 Futuro da Solução**
- **Chatbots corporativos** com respostas baseadas em documentos internos
- **Automação de relatórios regulatórios** (Bacen, CVM)
- **Sistema de recomendação** para melhores práticas baseado em casos passados

> "Não é sobre ter dados, é sobre **entender** e **agir** sobre eles. Essa solução coloca a inteligência no centro operacional do negócio." - CIO, Varejo Multinacional

---
## 👨‍💻 Expert

<p>
    <img 
      align=left 
      margin=10 
      width=80 
      src="https://avatars.githubusercontent.com/u/193035748?v=4&size=64"
    />
    <p>&nbsp&nbsp&nbspSilvia Fagundes de Sousa<br>
    &nbsp&nbsp&nbsp
    <a href="https://github.com/silvialibras">
    GitHub</a>&nbsp;|&nbsp;
    <a href="https://www.linkedin.com/in/
silvia-sousa-ba7a2531a/">LinkedIn</a>
&nbsp;|&nbsp;
    <a href="https://www.instagram.com/silviafagundess/">
Instagram</a>
&nbsp;|&nbsp;</p>
</p>
<br/><br/>
<p>


