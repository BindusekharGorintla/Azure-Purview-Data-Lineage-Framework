# Microsoft Purview Implementation in Azure

## Overview
This repo explores different ways to integrate **Microsoft Purview** with **Azure Databricks** for data lineage and governance.

---

## Approaches

### 1. Purview REST APIs
- **Pros**: Custom lineage via Service Principal, extend metadata, register new types.  
- **Cons**: Manual GUID extraction + curl scripts.  
- **Access**: Atlas API endpoint, Service Principal.  
- [Guide](https://piethein.medium.com/use-azure-purviews-rest-apis-for-creating-custom-lineage-ad8efacc6230)

---

### 2. PyApacheAtlas SDK
- **Pros**: Pythonic SDK, bulk loading, custom lineage, Excel integration.  
- **Cons**: Manual GUID extraction + Python scripts.  
- **Access**: Azure Identity + CLI, Service Principal.  
- [Repo](https://github.com/wjohnson/pyapacheatlas)

---

### 3. Unity Catalog Lineage
- **Pros**: Import lineage via REST API.  
- **Cons**: JSON → CSV conversion complexity.  
- [Docs](https://learn.microsoft.com/en-us/answers/questions/1315128/can-i-import-custom-lineage-from-a-json-file-in-pu)

---

### 4. Hybrid (REST/PyApacheAtlas + Python)
- **Pros**: Automates GUID extraction, reduces manual effort.  
- **Cons**: Development effort needed.  
- [Docs](https://learn.microsoft.com/en-us/azure/databricks/data-governance/unity-catalog/data-lineage)

---

## Subtasks
- Input: Table name  
- Output: Lineage updated in Purview entity  
- Steps:  
  1. Get lineage from Databricks (API + Service Principal)  
  2. Get entity details from Purview (Atlas API)  
  3. Match GUIDs, prepare JSON  
  4. Update lineage via Purview REST API  

---

## Broad Implementation
1. Setup data sources  
2. Connect Databricks with Service Principal  
3. Scan + ingest into Purview  
4. Configure classifications  
5. Enable auto/manual lineage  
6. Build Business Glossary  
7. Collaborate with teams for metadata curation  

---

## Outcome
- Multiple approaches for lineage integration  
- Trade-offs documented (manual vs automated)  
- Portfolio-ready project for **enterprise data governance**
