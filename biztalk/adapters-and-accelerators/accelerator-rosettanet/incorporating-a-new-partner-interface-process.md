---
title: Vous incorporez un nouveau Partner Interface Process | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, PIP schemas
- PIP schemas
- PIP schemas, deploying
- PIP schemas, downloading
- creating, PIP schemas
- PIP schemas, creating
ms.assetid: 6a5fcbcb-c6aa-40c0-bcca-dd0c391e7f42
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bf80c8bb577f4ddc8aec3282805714a830c7d23
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="incorporating-a-new-partner-interface-process"></a>Vous incorporez un nouveau Partner Interface Process
Vous pouvez incorporer un nouveau schéma de RosettaNet processus PIP (Partner Interface) dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] assemblys. Pour faire en :  
  
-   Télécharger le schéma PIP sur le site Web de RosettaNet à [http://go.microsoft.com/fwlink/?linkid=33859](http://go.microsoft.com/fwlink/?linkid=33859).  
  
-   Déploiement du schéma à [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] dans le cadre de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] assembly RNPIPs ou dans le cadre d’une séparée [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] assembly. Pour plus d’informations, consultez [extension de BTARN avec un nouveau PIP](../../adapters-and-accelerators/accelerator-rosettanet/extending-btarn-with-a-new-pip.md).  
  
-   Création d’un nouveau paramètre de Configuration de processus dans le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion. Pour plus d’informations, consultez [comment créer ou modifier une Configuration de processus](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).  
  
 Le schéma téléchargé est généralement au format .dtd, avec une spécification PIP d’accompagnement de l’organisation RosettaNet sous forme de fichier .doc. Le processus d’étendre le pipeline pour utiliser le nouveau schéma inclut la conversion du fichier .dtd PIP dans un fichier .xsd.  
  
 Lorsque vous installez [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK inclut un nombre de schémas XSD. Vous pouvez trouver ces schémas dans le \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\Schemas dossier. BTARN génère ces schémas dans un fichier RNPIPs.dll. Si vous devez modifier l’un de ces schémas, vous devez ouvrir le projet RNPIPs dans le même dossier, modifier le schéma dans l’Éditeur BizTalk, puis recompiler et redéployer l’assembly. Une fois que vous redéployez le fichier RNPIPs.dll, vous devez redéployer le pipeline qui utilise le schéma. Ce processus vous permet d’incorporer un nouveau schéma dans BTARN, mais il est plus facile d’étendre le pipeline pour inclure le nouveau schéma.  
  
### <a name="to-obtain-the-pip-schema"></a>Pour obtenir le schéma PIP  
  
-   Dans Internet Explorer, accédez au site Web de RosettaNet à [http://go.microsoft.com/fwlink/?linkid=33859](http://go.microsoft.com/fwlink/?linkid=33859).  
  
## <a name="see-also"></a>Voir aussi  
 [Extension de BTARN avec un nouveau processus PIP](../../adapters-and-accelerators/accelerator-rosettanet/extending-btarn-with-a-new-pip.md)