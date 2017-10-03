---
title: "Étape 6 : Configurer EDI-AS2 emplacement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 167f8ba2-d38b-4088-863b-2bd90c2a12a2
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4bbf1fce88301960a28c19fa20c9996282ce4619
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-6-configure-the-edi-as2-receive-location"></a>Étape 6 : Configurer EDI-AS2 emplacement de réception
![Étape 6 sur 11](../core/media/tut-step6-of-11.gif "Tut_Step6_of_11")  
  
 Au cours de cette étape, vous allez configurer un emplacement de réception unidirectionnel qui reçoit le message EDI du tiers Fabrikam. Cet emplacement de réception utilise le pipeline de réception AS2EdiReceive pour traiter le message EDI/AS2 entrant. Le message est envoyé vers l'emplacement de réception par l'application sender.exe via le répertoire virtuel Contoso à l'aide de l'extension ISAPI BTSHTTPReceive.dll.  
  
 Dans ce didacticiel, vous allez configurer un port d'envoi dynamique pour envoyer la réponse MDN de manière asynchrone. Dans ce scénario, un seul port de réception unidirectionnel est nécessaire. Vous pouvez toutefois également modifier l'exécutable Sender.exe pour envoyer un message AS2 spécifiant un MDN synchrone. Vous devrez alors créer un port de réception de requête-réponse bidirectionnel pour renvoyer le MDN. Pour plus d’informations, consultez la section « pour tester la solution » de [procédure pas à pas (AS2) : réception d’EDI via AS2 avec un MDN synchrone](../core/walkthrough-as2-receiving-edi-over-as2-with-a-synchronous-mdn.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-create-the-biztalk-http-receive-location"></a>Pour créer l'emplacement de réception HTTP BizTalk  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, sous le nœud BizTalk Application 1, avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.  
  
2.  Nommez le port de réception **Receive_AS2**.  
  
3.  Cliquez sur **emplacements de réception** dans l’arborescence de la console, puis cliquez sur **nouveau**.  
  
4.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue, le nom de votre emplacement de réception **Receive_AS2**, sélectionnez **HTTP** pour **Type**, puis Cliquez sur **configurer**.  
  
5.  Dans le **propriétés du Transport HTTP** boîte de dialogue, entrez **/Contoso/BTSHTTPReceive.dll** pour **répertoire virtuel assorti de l’extension ISAPI**. Désactivez **un descripteur de corrélation de retour en cas de réussite** et sélectionnez **suspendre les requêtes ayant échoué**. Cliquez sur **OK**.  
  
6.  Sélectionnez **AS2EdiReceive** pour le **Pipeline de réception**. Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.  
  
    > [!NOTE]
    >  Le pipeline de réception AS2EdiReceive effectue le décodage AS2 et le désassemblage EDI.  
  
7.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur **emplacements de réception** sous le nœud BizTalk Application 1, avec le bouton droit **Receive_AS2**, puis cliquez sur **activer** .  
  
## <a name="next-steps"></a>Étapes suivantes  
 Configurer le port d’envoi (**Send_Asynch_MDN**) port d’envoi pour renvoyer le MDN asynchrone à Fabrikam, comme décrit dans [étape 7 : configurer le Port d’envoi MDN](../core/step-7-configure-the-mdn-send-port.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Réception des Messages AS2 par BizTalk Server](../core/how-biztalk-server-receives-as2-messages.md)   
 [Configuration d’un Port de réception des Messages via AS2](../core/configuring-a-receive-port-for-messages-over-as2.md)