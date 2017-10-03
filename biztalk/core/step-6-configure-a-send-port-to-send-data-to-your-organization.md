---
title: "Étape 6 : Configurer un Port d’envoi pour envoyer des données à votre organisation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 796570ca-8178-4679-9213-d67a2a189bf9
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b513725024aec755515ccac998745220ee5dfa7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-6-configure-a-send-port-to-send-data-to-your-organization"></a>Étape 6 : Configurer un Port d’envoi pour envoyer des données à votre organisation
![Étape 6 de 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-6of9.gif "Step_6of9")  
  
 Cette étape permet de configurer un port d'envoi pour envoyer le message 850 depuis [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] au tiers OrderSystem qui représente votre organisation. Ce port d’envoi s’applique le **Inbound4010850_to_OrderFile** table, transformer le message de sortie à partir du format du message d’entrée au format spécifié dans le mappage.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-a-send-port-for-the-850-message"></a>Pour configurer un port d'envoi pour le message 850  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur **Pipelines**, puis cliquez sur **Actualiser**.  
  
    > [!NOTE]
    >  L'actualisation de la liste de pipelines peut être nécessaire pour sélectionner le pipeline SendOrderFilePipeline pour le port d'envoi que vous allez créer.  
  
2.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Entrez `toOrderSystem`.|  
    |**Type**|Sélectionnez **fichier**.|  
    |**Configurer**|Cliquez sur **configurer**.|  
  
    > [!NOTE]
    >  Le type de transport du port d'envoi est FILE car le message test est un fichier plat envoyé dans un dossier.  
  
4.  Dans le **propriétés du Transport FILE** boîte de dialogue zone, procédez comme suit, puis sur **OK**:  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Dossier de destination**|Cliquez sur **Parcourir**et dans le **rechercher un dossier** boîte de dialogue, accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer tutorial\processedi_testlocations\scenario A\toOrderSystem|  
    |**Nom de fichier**|Entrez `%MessageID%.txt`, puis cliquez sur **OK**.|  
  
    > [!NOTE]
    >  La valeur définie pour le **nom de fichier** propriété garantit que le fichier de sortie aura une extension .txt.  
  
5.  Dans le **propriétés de Port d’envoi** boîte de dialogue, pour **pipeline d’envoi**, sélectionnez **SendOrderFilePipeline**.  
  
    > [!NOTE]
    >  Le **SendOrderFilePipeline** pipeline inclut un assembleur de fichier plat qui assemble le fichier de sortie .txt, à l’aide des données mappées depuis le message 850 d’entrée d’envoi. Comme le fichier de sortie est un fichier .txt, il ne figure pas dans le rapport État de l'échange/de l'accusé de réception.  
  
6.  Dans l’arborescence de la console, cliquez sur **filtres**, puis procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Propriété**|Sélectionnez **BTS. ReceivePortName**.|  
    |**Opérateur**|Sélectionnez  **==** .|  
    |**Valeur**|Entrez `ReceiveEDI_fromTHEM_A`.|  
    |**Regrouper par**|Sélectionnez **et**.|  
    |**Propriété**|Sur la ligne suivante, sélectionnez **BTS. MessageType**.|  
    |**Opérateur**|Sélectionnez **! =**.|  
    |**Valeur**|Entrez `http://schemas.microsoft.com/Edi/X12#X12_997_Root`.|  
  
    > [!NOTE]
    >  Le filtre vérifie que le port d'envoi récupère les messages reçus par l'emplacement de réception Receive_EDI_fromTHEM_A, et que le port d'envoi récupère uniquement les messages 850, et non les accusés de réception 997.  
  
7.  Dans l’arborescence de la console, cliquez sur **OutboundMaps**. Dans le **mappages sortants** volet, dans le **carte** colonne, sur la première ligne, sélectionnez **Inbound4010850_to_OrderFile**. (L’entrée dans le **Document Source** colonne sera X12_00401_850.)  
  
    > [!NOTE]
    >  Cette étape permet de s’assurer que le message de sortie se compose uniquement des données mappées depuis le message d’entrée en fonction de la **Inbound4010850_to_OrderFile** carte.  
  
8.  Cliquez sur **OK**.  
  
9. Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur **Ports d’envoi**. Avec le bouton droit **toOrderSystem**, puis cliquez sur **Démarrer** pour inscrire et démarrer le port.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Configurer le port d’envoi (**toTHEM_997**) pour envoyer le 997 accusé de réception vers Fabrikam, comme décrit dans [étape 7 : configurer un Port d’envoi pour envoyer l’accusé de réception à votre partenaire commercial](../core/step-7-configure-a-send-port-to-send-the-acknowledgment-to-trading-partner.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration d’un Port d’envoi statique pour envoyer des échanges EDI et les accusés de réception](../core/configuring-a-static-send-port-to-send-edi-interchanges-and-acknowledgments.md)