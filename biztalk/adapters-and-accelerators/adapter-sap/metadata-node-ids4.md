---
title: ID de nœud de métadonnées de l’adaptateur mySAP dans le Pack d’adaptateurs BizTalk | Documents Microsoft
description: Métadonnées, search, les types de nœuds de récupération et les identificateurs utilisés dans les composants SAP qui sont exposées dans l’adaptateur mySAP - Pack de l’adaptateur BizTalk (LOB)
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46385060-f56a-4e06-9122-b75808776716
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 138e46b198df48348dcef35662589f6a3c2e317a
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="node-types-and-ids-for-the-sap-adapter"></a>Types de nœuds et ID de l’adaptateur SAP

## <a name="metadata-node-types-and-ids"></a>Types de nœuds de métadonnées et des ID
Le tableau suivant répertorie le type de nœud et l’ID de nœud pour les artefacts SAP qui le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] surfaces. L’ID de nœud est le chemin d’accès absolu du nœud qui est utilisé dans le **IMetadataRetrievalContractBrowse**, **recherche**, et **GetMetadata** méthodes.  
  
|Nom complet de l’objet|Type de nœud|ID de nœud|  
|---------------------------|---------------|-------------|  
|RFC|CATÉGORIE|[VERSION]/RFCSECTION|  
|[RFC_APPL_GROUP_NAME]|CATÉGORIE|[VERSION]/RFCGROUP/[RFC_APPL_GROUP_ID]|  
|[RFC_NAME]|OPERATION|[VERSION]/Rfc/[RFC_NAME]|  
|RfcGetAttributes|OPERATION|[VERSION]/RfcApi/RfcGetAttributes|  
|TRFC|CATÉGORIE|[VERSION]/TRFCSECTION|  
|[TRFC_APPL_GROUP_NAME]|CATÉGORIE|[VERSION]/TRFCGROUP/[TRFC_APPL_GROUP_ID]|  
|[TRFC_NAME]|OPERATION|[VERSION]/TRfc/[TRFC_NAME]|  
|RfcConfirmTransID|OPERATION|[VERSION]/RfcApi/RfcConfirmTransID|  
|BAPI|CATÉGORIE|[VERSION]/BAPISECTION/000001|  
|[BAPI_APPL_GROUP_NAME]|CATÉGORIE|[VERSION]/BAPISECTION/[ BAPI_APPL_GROUP_NODE_ID]|  
|[BUSINESS_OBJECT_NAME]|CATÉGORIE|[VERSION]/BAPIOBJ/[BUSOBJ_TYPE]|  
|[BUSINESS_OBJECT_METHOD]|OPERATION|[VERSION]/BAPIOBJ/[BUSOBJ_TYPE]/[BUSOBJ_METHOD]/[FUNCTION_MODULE]|  
|IDOC|CATÉGORIE|[VERSION]/IDOCSECTION|  
|[IDOC_MSG_TYPE_NAME]|CATÉGORIE|[VERSION]/IDOCMESTYP/[IDOC_MSG_TYPE_NAME]|  
|([IDOC_TYPE_NAME]) ([IDOC_CIMTYPE])|CATÉGORIE|[VERSION]/IDOCCIMTYP/[IDOC_TYPE_NAME]/[IDOC_CIMTYPE]/[FIRST_IDOC_REL_NO]|  
|([IDOC_TYPE_NAME].V[IDOC_VERSION]) ([IDOC_CIMTYPE]) ([IDOC_REL_NO])|CATÉGORIE|[VERSION]/IDOCCIMVER/[IDOC_VERSION]/[IDOC_TYPE_NAME]/[IDOC_CIMTYPE]/[IDOC_REL_NO]|  
|Send|OPERATION|[VERSION]/Idoc/[IDOC_VERSION]/[IDOC_TYPE_NAME]/[IDOC_CIMTYPE]/[IDOC_REL_NO]/Send|  
|SendIdoc|OPERATION|[VERSION]/Idoc/SendIdoc|  
|Recevoir|OPERATION|[VERSION]/Idoc/[IDOC_VERSION]/[IDOC_TYPE_NAME]/[IDOC_CIMTYPE]/[IDOC_REL_NO]/Receive|  
|ReceiveIdoc|OPERATION|[VERSION]/Idoc/ReceiveIdoc|  
  
 [VERSION] = la chaîne de version ; par exemple, http://Microsoft.LobServices.Sap/2007/03.  
  
 [RFC_APPL_GROUP_NAME] = le nom d’un groupe de l’application ; par exemple, ventes.  
  
 [ID RFC_APPL_GROUP_] = l’ID associé à un groupe d’applications dans SAP ; par exemple, V (ventes).  
  
 [RFC_NAME] = le nom d’une commande RFC ; par exemple, RFC_GET_SYSTEM_INFO.  
  
 [TRFC_APPL_GROUP_NAME] = le nom d’un groupe de l’application ; par exemple, ventes. Cela est identique à celui du groupe d’application pour les documents RFC.  
  
 [ID TRFC_APPL_GROUP_] = l’ID associé à un groupe d’applications dans SAP ; par exemple, V (ventes). Cela est identique à l’ID de RFC.  
  
 [TRFC_NAME] = le nom d’un tRFC ; par exemple, RFC_GET_SYSTEM_INFO. Ceci est le même que le nom de la RFC.  
  
 [BAPI_APPL_GROUP_NAME] = le nom du groupe BAPI comme dans l’Explorateur de BAPI dans SAP. Par exemple, ventes et la Distribution.  
  
 [BAPI_APPL_GROUP_NODE_ID] = l’ID associé au nœud correspondant dans l’arborescence de l’Explorateur BAPI SAP ; Par exemple, 3253 pour les ventes et de Distribution. Notez qu’il peut y avoir plusieurs nœuds de groupe sous un nœud de groupe BAPI donné. Par exemple, les ventes et la Distribution nœud possède un autre nœud de groupe sous celui-ci appelée ventes (nœud ID 3375).  
  
 [BUSINESS_OBJECT_NAME] = le nom d’un objet métier ; par exemple, Sales Order.  
  
 [BUSOBJ_TYPE] = type d’objet métier dans SAP ; par exemple BUS2032 pour l’objet métier Sales Order.  
  
 [BUSINESS_OBJECT_METHOD] = le nom d’une méthode d’objet métier ; par exemple, GETLIST pour l’objet métier Sales Order.  
  
 [MODULE de fonction] = le module de fonction de la SAP pour la méthode d’objet métier ; par exemple, BAPI_SALESORDER_GETLIST pour la méthode GETLIST de l’objet métier de vente.  
  
 [IDOC_MSG_TYPE_NAME] = le nom d’un type de message IDOC ; par exemple, les commandes.  
  
 [IDOC_TYPE_NAME] = le nom du type IDOC ; par exemple, ORDERS05.  
  
 [IDOC_CIMTYPE] = Type CIM IDOC (extension) ; par exemple, Z1ORDERS.  
  
 [FIRST_IDOC_REL_NO] = le numéro de version IDOC minimal pour un type IDOC particulier ; par exemple, 46 bis pour ORDERS05 dans un système SAP spécifique.  
  
 [IDOC_VERSION] = numéro de version IDOC la mise en production ; 2 pour relâchez 2 IDOC et 3 pour 3 IDOC...  
  
 [IDOC_REL_NO] = IDOC le numéro de version ; par exemple 46 bis, 46 ter ou 620.  
  
## <a name="metadata-search-node-ids"></a>ID de nœud de recherche de métadonnées  
 Recherche de métadonnées est une puissante fonctionnalité le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] surfaces dans le cadre de son **IMetadataRetrievalContract** interface. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise cette fonctionnalité pour prendre en charge la recherche les artefacts SAP suivants.  
  
|Nom complet de l’objet|ID de nœud| Description|  
|---------------------------|-------------|-----------------|  
|/RFC|[VERSION]/RFCSECTION|Retourne toutes les opérations de RFC qui correspondent à l’expression de recherche.|  
|/RFC/[RFC_APPL_GROUP_NAME]|[VERSION]/RFCGROUP/[RFC_APPL_GROUP_NAME]|Retourner les opérations de RFC dans le groupe d’applications qui correspondent à l’expression de recherche.|  
|/TRFC|[VERSION]/TRFCSECTION|Retourne toutes les opérations de RFC qui correspondent à l’expression de recherche.|  
|/TRFC/[TRFC_APPL_GROUP_NAME]|[VERSION]/TRFCGROUP/[TRFC_APPL_GROUP_NAME]|Retourner les opérations de RFC dans le groupe d’applications qui correspondent à l’expression de recherche.|  
|/BAPI|[VERSION]/BAPISECTION|Retourne toutes les interfaces BAPI qui correspondent à l’expression de recherche.|  
|/IDOC|[VERSION]/IDOCSECTION|Retourner tous les IDOC qui correspondent à l’expression de recherche.|  
  
 Le tableau suivant répertorie les caractères génériques caractères qui le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge dans les expressions de recherche.  
  
|Caractère spécial|Interpretation|  
|-----------------------|--------------------|  
|signe plus (+)|Correspond à exactement un caractère.<br /><br /> Par exemple, A + correspond à AB, CA, AD, et ainsi de suite.|  
|astérisque (*)|Correspond à zéro ou plusieurs caractères ; par exemple, « A * » correspond à « A », « AB », « ABC » et ainsi de suite.|  
  
## <a name="metadata-retrieval-node-ids"></a>ID de nœud de la récupération de métadonnées  
 Le tableau suivant résume les caractéristiques des métadonnées retournées par [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
|Artefact|Caractéristiques des métadonnées|  
|--------------|------------------------------|  
|RFC|-Nom de la RFC.<br />-Les paramètres d’importation, d’exportation, la modification et table RFC.<br />-Types de données du paramètre RFC.<br />-Longueur de champ de paramètre RFC mappée à la facette maxLength<br />-Paramètre obligatoire de RFC mappé à la facette minOccurs = 1<br />-Paramètre facultatif de RFC mappé à la facette minOccurs = 0<br />-Le paramètre RFC contrainte NULL mappé à la facette isNillable = true. Cela signifie que l’adaptateur ne passez pas ce paramètre pour le système SAP.<br />-La RFC lui-même est l’opération.|  
|TRFC|Identique à la RFC à l’exception<br /><br /> -Paramètres d’importation RFC ne sont pas signalées. Étant donné que tRFC est asynchrone, aucun paramètre de sortie n’est signalées.|  
|BAPI|-Nom d’objet métier<br />-Nom de la méthode d’objet métier<br />-Identique à celui des caractéristiques RFC|  
|IDOC|Type IDOC<br /><br /> CIMType<br /><br /> Numéro de version IDOC<br /><br /> Version IDOC<br /><br /> Champs d’enregistrement de contrôle IDOC mappés à un type complexe EDI_DC<br /><br /> IDOC enregistrement de segments et les champs du segment mappés à un type complexe EDI_DD<br /><br /> Relations parent-enfant de segment<br /><br /> Paramètre obligatoire du segment IDOC mappé à la valeur minOccurs = 1<br /><br /> IDOC segment paramètre facultatif mappé à la valeur minOccurs = 0<br /><br /> Nom du champ IDOC segment en-tête<br /><br /> Type de données du champ IDOC segment en-tête<br /><br /> Nom du champ segment IDOC<br /><br /> Type de données de champ de segment IDOC<br /><br /> Énumérations de valeur de champ de segment IDOC<br /><br /> IDOC segment champ valeurs minimales et maximales (plages) **Remarque :** lorsque IDOC un segment champ contient la liste des valeurs min, il est présenté comme une énumération. Si le champ de segment IDOC contient les valeurs minimale et maximale, il est présenté comme une chaîne sans des éléments de l’énumération ou de la plage.|  
  
 Pour plus d’informations sur le format des métadonnées qui le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] expose pour les artefacts et les opérations sur le système SAP, consultez [Messages et des schémas de Message pour l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md).  
  
