---
title: "Étape 5 : Configurer un Port de réception et l’emplacement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43fc8d12-5fde-4ddf-a7f0-770f078ba66b
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8ec436657aefaceb71207d37808936aa6eaa1a3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-5-configure-a-receive-port-and-receive-location"></a>Étape 5 : Configurer un Port de réception et l’emplacement de réception
![L’étape 5 de 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-5of9.gif "Step_5of9")  
  
 Cette étape permet de configurer un port et un emplacement de réception pour recevoir un message 850 dans le dossier créé pour le tiers Fabrikam.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-a-receive-port-and-receive-location-for-receiving-the-850-message"></a>Pour configurer un port et un emplacement de réception permettant de recevoir un message 850  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez **Administration de BizTalk Server**, **groupe BizTalk**, **Applications**, puis **BizTalk Application 1**. Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.  
  
2.  Dans la boîte de dialogue Propriétés du Port de réception, dans le **nom** , saisissez `ReceiveEDI_fromTHEM_A`.  
  
3.  Cliquez sur **emplacements de réception** dans l’arborescence de la console, puis cliquez sur **nouveau** dans le volet droit.  
  
4.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** , saisissez `fromTHEM_4010_850`.  
  
5.  Pour **Type**, sélectionnez **fichier**, puis cliquez sur **configurer**.  
  
    > [!NOTE]
    >  Le type de transport de l'emplacement de réception est FILE, car le message test est un fichier plat envoyé dans un dossier.  
  
6.  Dans le **propriétés du Transport FILE** boîte de dialogue, cliquez sur le **Parcourir** situé en regard du **dossier de réception** champ. Dans le **rechercher un dossier** boîte de dialogue, accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\fromTHEM, puis cliquez sur **OK**.  
  
7.  Dans le **propriétés du Transport FILE** boîte de dialogue, choisissez le **masque de fichier** à  **\*.txt** et cliquez sur **OK**.  
  
    > [!NOTE]
    >  Le masque de fichier est défini sur *.txt, car le message test d'entrée est un fichier texte, à savoir SamplePO.txt.  
  
8.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Pipeline de réception** champ, sélectionnez **EdiReceive**.  
  
    > [!NOTE]
    >  Le pipeline de réception permettant de recevoir des échanges EDI, à l'exception de ceux envoyés via le transport AS2, est le pipeline EdiReceive. (Le pipeline de réception AS2EdiReceive permet de recevoir des échanges EDI envoyés via le transport AS2.)  
  
    > [!NOTE]
    >  Si EdiReceive ne figure pas dans la liste déroulante des pipelines de réception, cela signifie que votre application ne comporte peut-être pas de référence à l'application BizTalk EDI. Pour ajouter la référence, consultez [comment ajouter une référence à l’Application EDI de BizTalk Server](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).  
  
9. Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.  
  
    > [!NOTE]
    >  Le compte disposant des autorisations de connexion au service BizTalk doit également recevoir les autorisations d'accès total au dossier de réception associé à l'emplacement de réception fromTHEM_4010_850 ([!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\ProcessEDI_TestLocations\fromTHEM). Si ce n'est pas le cas, un message d'erreur s'affichera lorsque vous tenterez d'activer l'emplacement de réception. Pour modifier les autorisations d’accès au dossier de réception, accédez à l’onglet sécurité dans les **propriétés** boîte de dialogue pour ce dossier dans l’Explorateur Windows.  
  
10. Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur **emplacements de réception**, avec le bouton droit **fromTHEM_4010_850**, puis cliquez sur **activer**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Configurer le port d’envoi (**toOrderSystem**) pour envoyer le message 850 à OrderSystem, comme décrit dans [étape 6 : configurer un Port d’envoi pour envoyer des données à votre organisation](../core/step-6-configure-a-send-port-to-send-data-to-your-organization.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration d’un Port pour recevoir des Messages EDI et les accusés de réception](../core/configuring-a-port-to-receive-edi-messages-and-acknowledgments.md)