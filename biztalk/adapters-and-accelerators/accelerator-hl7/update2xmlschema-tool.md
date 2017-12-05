---
title: Outil de Update2XMLSchema | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 2.XML schemas, Update2XMLSchema tool
- schemas, Update2XMLSchema tool
- Update2XMLSchema tool
- Update2XMLSchema tool, syntax
ms.assetid: fd861e2f-ebda-427f-bd52-a2f05b7e22da
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e0f5a33b8951d1f02cf0504ba833b35adf275834
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="update2xmlschema-tool"></a>Outil de Update2XMLSchema
L’outil Update2XMLSchema vous permet de modifier les schémas HL7 2. pour fonctionner avec l’Éditeur BizTalk. Cela est nécessaire car certains schémas XML de 2 HL7 ne fonctionnent pas correctement dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] sans modification. Après avoir modifié les schémas, l’outil les place dans le dossier schémas où [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] est installé, par exemple,  *\<lecteur\>*: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\Templates\Schemas.  
  
 Vous devez mettre à jour manuellement certains champs des schémas qui résultent de l’exécution de l’outil Update2XMLSchema. Consultez [mises à jour manuelles nécessaires](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md) pour obtenir la liste de ces schémas.  
  
## <a name="syntax"></a>Syntaxe  
 Cet outil se trouve dans  *\<lecteur\>*: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\2XML utilitaires. Vous exécutez cet outil à l’invite de commandes avec la commande suivante :  
  
```  
Update2XMLSchema /s /v  
```  
  
 Le tableau suivant répertorie les paramètres à utiliser avec cette commande.  
  
|Paramètre|Nom|Valeur|  
|---------------|----------|-----------|  
|*S*|Source|Chemin d’accès complet des schémas HL7 d’origine|  
|*V*|Version|La version des schémas XML 2 : 2.3.1, 2.4 ou 2.5|  
  
## <a name="example"></a>Exemple  
  
-   Si vous souhaitez modifier des schémas XML de la version 2.3.1 2 situés dans le répertoire c:\231XML\v231\xsd, vous indiquez la commande suivante à l’invite de commandes :  
  
```  
Update2XMLSchema /s c:\231XML\v231\xsd /v 2.3.1  
```  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Mises à jour manuelles nécessaires](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md)