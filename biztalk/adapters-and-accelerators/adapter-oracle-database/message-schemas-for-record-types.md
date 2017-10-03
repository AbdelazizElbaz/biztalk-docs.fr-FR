---
title: "Schémas de message pour les Types d’enregistrements | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RECORD types, message schemas for
- RECORD types, support for
ms.assetid: 637c42f2-eed0-4941-a6cd-7e03d01088b8
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9022274041e06ad8ccc3f5243715d44d2b64282
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-record-types"></a><span data-ttu-id="12eee-102">Schémas de message pour les Types d’enregistrements</span><span class="sxs-lookup"><span data-stu-id="12eee-102">Message Schemas for RECORD Types</span></span>
<span data-ttu-id="12eee-103">Types d’enregistrements Oracle sont les types de données structurées PL/SQL qui se composent d’une ou plusieurs des types de base de données simple ou structuré.</span><span class="sxs-lookup"><span data-stu-id="12eee-103">Oracle RECORD types are structured PL/SQL data types that consist of one or more simple or structured database types.</span></span> <span data-ttu-id="12eee-104">Types d’enregistrements sont principalement utilisées dans les procédures stockée PL/SQL et des fonctions pour envoyer et recevoir des données hiérarchiques.</span><span class="sxs-lookup"><span data-stu-id="12eee-104">RECORD types are primarily used in PL/SQL stored procedures and functions to send and receive hierarchical data.</span></span>  
  
 <span data-ttu-id="12eee-105">Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] prend en charge les types d’enregistrement de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="12eee-105">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] supports RECORD types in the following manner:</span></span>  
  
-   <span data-ttu-id="12eee-106">Types d’enregistrements sont exposés en tant que types complexes.</span><span class="sxs-lookup"><span data-stu-id="12eee-106">RECORD types are surfaced as complex types.</span></span>  
  
-   <span data-ttu-id="12eee-107">Types d’enregistrement peuvent être imbriqué (enregistrement d’un enregistrement).</span><span class="sxs-lookup"><span data-stu-id="12eee-107">RECORD types can be nested (record in a record).</span></span>  
  
-   <span data-ttu-id="12eee-108">Types d’enregistrement peuvent être déclarés en tant que TABLE % ROWTYPE paramètres dans les procédures stockées et fonctions.</span><span class="sxs-lookup"><span data-stu-id="12eee-108">RECORD types can be declared as TABLE%ROWTYPE parameters in stored procedures and functions.</span></span>  
  
-   <span data-ttu-id="12eee-109">Types d’enregistrements peuvent être déclarés en tant que paramètres de TYPE d’enregistrement dans les packages de PL/SQL ; par exemple, `TYPE rec_type1 IS RECORD(name varchar2(100), age number(3));`.</span><span class="sxs-lookup"><span data-stu-id="12eee-109">RECORD types can be declared as TYPE of RECORD parameters in PL/SQL packages; for example, `TYPE rec_type1 IS RECORD(name varchar2(100), age number(3));`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="12eee-110">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne prend pas en charge les types BFILE en tant que membres de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="12eee-110">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support BFILE types as RECORD members.</span></span>  
  
 <span data-ttu-id="12eee-111">Lorsqu’un paramètre de type d’enregistrement est utilisé dans une procédure stockée ou une fonction, il est compatible avec l’espace de noms de cette opération.</span><span class="sxs-lookup"><span data-stu-id="12eee-111">When a RECORD type parameter is used in a stored procedure or a function, it is qualified with the namespace of that operation.</span></span> <span data-ttu-id="12eee-112">Le code XML suivant montre la structure d’un type d’enregistrement dans un message :</span><span class="sxs-lookup"><span data-stu-id="12eee-112">The following XML shows the structure of a RECORD type in a message:</span></span>  
  
```  
<[REC_PARAM_NAME]>  
  <[FIELD_NAME1] xmlns="[OPERATION_NAMESPACE]">value1</[FIELD_NAME1]>  
  <[FIELD_NAME2] xmlns="[OPERATION_NAMESPACE]">value2</[FIELD_NAME2]>  
  …  
</[REC_PARAM_NAME]>  
```  
  
 <span data-ttu-id="12eee-113">[REC_PARAM_NAME] est le nom du paramètre d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="12eee-113">[REC_PARAM_NAME] is the name of the RECORD parameter.</span></span>  
  
 <span data-ttu-id="12eee-114">[Nom_champ] est le nom d’un champ dans le type d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="12eee-114">[FIELD_NAME] is the name of a field in the RECORD type.</span></span>  
  
 <span data-ttu-id="12eee-115">[OPERATION_NAMESPACE] est l’espace de noms de la procédure stockée ou fonction dans laquelle le paramètre d’enregistrement est utilisé.</span><span class="sxs-lookup"><span data-stu-id="12eee-115">[OPERATION_NAMESPACE] is the namespace of the stored procedure or function in which the RECORD parameter is being used.</span></span>  
  
 <span data-ttu-id="12eee-116">Le code XML suivant montre la structure d’un paramètre de type d’enregistrement avec un champ de type enregistrement imbriqué :</span><span class="sxs-lookup"><span data-stu-id="12eee-116">The following XML shows the structure of a RECORD type parameter with a nested RECORD type field:</span></span>  
  
```  
<[REC_PARAM_NAME]>    
  <[FIELD_NAME1] xmlns="[OPERATION_NAMESPACE]">value1</[FIELD_NAME1]>  
  <[FIELD_NAME2] xmlns="[OPERATION_NAMESPACE]">value2</[FIELD_NAME2]>  
  <[REC_PARAM_NAME2]>  
    <[FIELD_NAME1] xmlns="[OPERATION_NAMESPACE]">value1</[FIELD_NAME1]>  
    <[FIELD_NAME2] xmlns="[OPERATION_NAMESPACE]">value1</[FIELD_NAME2]>  
    …  
  </[REC_PARAM_NAME2]>  
  …  
</[REC_PARAM_NAME]>  
```  
  
## <a name="see-also"></a><span data-ttu-id="12eee-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12eee-117">See Also</span></span>  
 [<span data-ttu-id="12eee-118">Messages et des schémas de Message pour l’adaptateur BizTalk pour base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="12eee-118">Messages and Message Schemas for BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)