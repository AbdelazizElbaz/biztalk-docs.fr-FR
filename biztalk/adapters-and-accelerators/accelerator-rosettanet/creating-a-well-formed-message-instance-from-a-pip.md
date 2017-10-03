---
title: "Création d’une Instance de Message bien formée à partir d’une adresse PIP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message templates
- PIPs, message templates
ms.assetid: fed3698c-25d9-40ca-878a-60171f425bec
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e16020afb17d17c8add8e973ade0cd0c5cfcbbc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-well-formed-message-instance-from-a-pip"></a>Création d'une instance de message bien formée à partir d'un processus PIP
Cette rubrique explique comment produire une instance de message bien formée. Vous pouvez générer un modèle pour une instance de message à partir du processus d'interface entres partenaires (PIP). Après avoir effectué cette opération, vous devez modifier ce modèle, afin qu'il soit bien formé, avant d'ajouter vos données.  
  
### <a name="to-generate-a-message-instance-template-from-the-pip"></a>Pour générer un modèle d'instance de message à partir du PIP  
  
1.  Démarrez **Microsoft Visual Studio 2012**.  
  
2.  Dans le menu **Fichier** , pointez sur **Ouvrir**, puis cliquez sur **Projet**.  
  
3.  Recherchez \< *lecteur*> \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNetSDK\Schemas, cliquez sur **RNPIPs.btproj**, puis cliquez sur **Ouvrir**.  
  
4.  Dans l'Explorateur de solutions, développez **RNPIPs**, puis cliquez avec le bouton droit sur le PIP pour lequel vous voulez créer une instance.  
  
5.  Cliquez sur **Générer l'instance**.  
  
    > [!NOTE]
    >  Cela génère un fichier qui porte le nom du PIP, avec « _output » ajouté au nom de fichier et dont l'extension est .xml. Indique l’endroit où une instruction dans le volet de sortie [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] a généré l’instance.  
  
### <a name="to-modify-the-message-instance-template"></a>Pour modifier le modèle d'instance de message  
  
1.  Dans [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorateur de solutions, recherchez le dossier contenant le fichier XML, double-cliquez sur le nom de fichier pour ouvrir le dossier.  
  
2.  Ajoutez, avant tout le reste du texte, une balise d'en-tête XML indiquant la version du code XML et le codage. Exemple :  
  
    ```  
    <?xml version="1.0" encoding="UTF-8" ?>  
    ```  
  
3.  Après la ligne que vous venez d'ajouter, ajoutez une ligne DOCTYPE indiquant le DTD. Par exemple, pour une instance de demande de bon de commande 3A4, la ligne serait la suivante :  
  
    ```  
    <!DOCTYPE Pip3A4PurchaseOrderRequest SYSTEM "3A4_MS_V02_02_PurchaseOrderRequest.dtd">  
    ```  
  
    > [!NOTE]
    >  Chaque instance de message doit inclure la ligne DOCTYPE à traiter.  
  
4.  Vous pouvez maintenant personnaliser cette instance de message pour répondre aux besoins de votre entreprise. Modifiez l'instance XML afin qu'elle n'utilise pas des préfixes d'espace de noms ou des espaces de noms XML.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)