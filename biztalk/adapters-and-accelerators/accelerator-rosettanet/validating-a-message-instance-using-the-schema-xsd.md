---
title: "Validation d’une Instance de Message en utilisant le schéma XSD | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schema XSD
- validating, messages
- messages, validating
- schemas, XSDs
ms.assetid: c4cbf6b4-130d-4e0f-840b-c8008fafac0b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50a4e0b08e3bbe9e29b3417fd6e53475fd98483c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="validating-a-message-instance-using-the-schema-xsd"></a>Validation d’une Instance de Message en utilisant le schéma XSD
Cette rubrique décrit comment valider une instance de message à l’aide d’un des fichiers XSD de schéma que Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] a intégré dans le fichier d’assembly RNPIPs.  
  
### <a name="to-validate-a-message-instance-using-the-schema-xsd"></a>Pour valider une instance de message en utilisant le schéma XSD  
  
1.  Démarrez **Microsoft Visual Studio 2012**.  
  
2.  Sur le **fichier**, pointez sur **ouvrir**, puis cliquez sur **projet**.  
  
3.  Recherchez  *\<lecteur >*\Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\Schemas, cliquez sur **RNPIPs.btproj**, puis cliquez sur **Ouvrir**.  
  
4.  Dans l’Explorateur de solutions, développez **RNPIPs**, cliquez sur le schéma XSD que vous souhaitez utiliser pour valider une instance de message, puis cliquez sur **propriétés**.  
  
5.  Dans la boîte de dialogue Pages de propriétés, cliquez sur **nom d’Instance d’entrée**, recherchez le dossier qui contient le fichier, sélectionnez le fichier d’instance de message XML, puis cliquez sur **ouvrir**.  
  
6.  Cliquez sur **OK**.  
  
7.  Dans l’Explorateur de solutions, cliquez sur le schéma XSD que vous souhaitez utiliser pour valider une instance de message, puis cliquez sur **valider l’Instance**.  
  
## <a name="see-also"></a>Voir aussi  
 [Modification d’un PIP existant dans RNPIPs](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md)   
 [Utilisation des adresses PIP](../../adapters-and-accelerators/accelerator-rosettanet/working-with-pips.md)