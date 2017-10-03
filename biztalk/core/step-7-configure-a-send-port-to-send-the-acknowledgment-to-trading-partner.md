---
title: "Étape 7 : Configurer un Port d’envoi pour envoyer l’accusé de réception à votre partenaire commercial | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a082870-894c-4f64-a575-3681d8a5c4ea
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 59d36aaaf33673095c664363da5b3417bbd1cde4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-7-configure-a-send-port-to-send-the-acknowledgment-to-your-trading-partner"></a>Étape 7 : Configurer un Port d’envoi pour envoyer l’accusé de réception à votre partenaire commercial
![Étape 7 de 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-7of9.gif "Step_7of9")  
  
 Dans cette étape, vous configurez un port d’envoi pour envoyer le message d’accusé de 997 réception généré par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à Fabrikam **toTHEM_997** dossier.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-a-send-port-that-subscribes-to-the-997-acknowledgment"></a>Pour configurer un port d'envoi abonné à l'accusé de réception 997  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
2.  Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Entrez `toTHEM_997`.|  
    |**Type**|Sélectionnez **fichier**.|  
    |**Configurer**|Cliquez sur **configurer**.|  
  
    > [!NOTE]
    >  Le type de transport du port d'envoi est FILE car l'accusé de réception 997 est un fichier plat envoyé dans un dossier.  
  
3.  Dans le **propriétés du Transport FILE** boîte de dialogue zone, procédez comme suit, puis sur **OK**:  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Dossier de destination**|Cliquez sur **Parcourir**et dans le **rechercher un dossier** boîte de dialogue, accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\ Scenario A\toTHEM_997.|  
    |**Nom de fichier**|Entrez `%MessageID%.txt`, puis cliquez sur **OK**.|  
  
    > [!NOTE]
    >  La valeur définie pour le **nom de fichier** propriété garantit que le fichier de sortie aura une extension .txt.  
  
4.  Dans le **propriétés de Port d’envoi** boîte de dialogue, pour **Pipeline d’envoi**, sélectionnez **EdiSend**.  
  
    > [!NOTE]
    >  Le pipeline d'envoi permettant d'envoyer des échanges EDI est le pipeline EdiReceive, excepté pour les échanges envoyés via le transport AS2. (Le pipeline d'envoi AS2EdiSend est utilisé pour envoyer des échanges EDI, remis via le transport AS2.)  
  
5.  Dans l’arborescence de la console, cliquez sur **filtres**, puis procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Propriété**|Sélectionnez **BTS. MessageType**.|  
    |**Opérateur**|Sélectionnez  **==** .|  
    |**Valeur**|Entrez **http://schemas.microsoft.com/Edi/X12#X12_997_Root**.|  
  
    > [!NOTE]
    >  Le filtre assure que le port d'envoi récupère les messages avec le type de message 997.  
  
6.  Cliquez sur **OK**.  
  
7.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur **Ports d’envoi**. Avec le bouton droit **toTHEM_997**, puis cliquez sur **Démarrer** pour inscrire et démarrer le port.  
  
8.  Dans la Console Administration de BizTalk Server, dans l’arborescence de la console, cliquez sur **paramètres de plateforme**, puis cliquez sur **Instances d’hôte**. Dans le volet des Instances d’hôte, cliquez sur **BizTalkServerApplication**, puis cliquez sur **redémarrer**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous créez un accord entre les deux partenaires commerciaux, comme décrit dans [étape 8 : configurer l’accord de partenariat commercial entre les Parties](../core/step-8-configure-the-trading-partner-agreement-between-the-parties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration d’un Port d’envoi statique pour envoyer des échanges EDI et les accusés de réception](../core/configuring-a-static-send-port-to-send-edi-interchanges-and-acknowledgments.md)