---
title: Message volumineux vers MSMQ | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, examples
- examples, MSMQ adapters
ms.assetid: 1fb87b46-5656-42c0-be99-8ab66e51bb4d
caps.latest.revision: "35"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e6a3fda3082260338bd387dfe84fe48c7aed565
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="large-message-to-msmq"></a>Message volumineux vers MSMQ
Le Message volumineux vers MSMQ sample montre comment envoyer un document .xml supérieure à 4 mégaoctets (Mo) à partir de Message Queuing (également appelé MSMQ) pour l’adaptateur MSMQ BizTalk à l’aide de la **MQSendLargeMessage** API implémentée par MQRTLarge.dll.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 L'exemple fonctionne comme suit :  
  
1.  Un utilisateur envoie un fichier .xml volumineux à une file d'attente sur un ordinateur local à l'aide de SendLargeMessage.exe.  
  
2.  [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] reçoit le fichier .xml volumineux depuis la file d'attente et le copie dans un répertoire local.  
  
 Diverses opérations de Message Queuing sont asynchrones. Que de nombreux appels d’API de MSMQ (par exemple, **MQSendLargeMessage**) retour à l’appelant avant l’opération demandée soit entièrement terminée.  
  
 MSMQ intègre un mécanisme qui renvoie des commentaires à l'application une fois l'opération terminée. Ce mécanisme inclut l'utilisation d'une file d'administration. MSMQ renvoie des commentaires sous forme de messages dans la file d'administration. La file d'administration à laquelle MSMQ renvoie des commentaires est spécifiée lors de l'appel de l'API MSMQ. Ainsi, par exemple, lors de l’envoi d’un message à l’aide de la **MQSendLargeMessage** API, l’application peut spécifier le nom de la file d’administration à l’aide de la **PROPID_M_ADMIN_QUEUE** sur le message de la propriété de message passé dans l’appel à **MQSendLargeMessage**. Même si l’application peut obtenir un code de retour réussi le **MQSendLargeMessage** appel, si le message d’opération d’envoi échoue, par la suite MSMQ écrit un message à cet effet dans la file d’attente d’administration spécifié.  
  
 Si l’application ne spécifie pas de file d’administration, un échec d’envoi entraîne la perte du message sans aucun diagnostic. Le message disparaît purement et simplement. Plusieurs situations d'erreur dans MSMQ peuvent avoir cet effet, par exemple, suite à l'envoi d'un message non transactionnel à une file d'attente transactionnelle.  
  
 Dans le cadre de cet exemple, il est important que le code spécifie un type de transaction dans l’appel à **MQSendLargeMessage** qui soit cohérent avec la prise en charge de la transaction spécifiée pour la file d’attente à laquelle le message est envoyé. Si ce n'est pas le cas et si aucune file d'administration n'est spécifiée (comme dans cet exemple), l'API MSMQ écarte le message envoyé sans le signaler (aucun code d'erreur n'est renvoyé à l'application, aucun diagnostic n'est écrit dans le journal des événements, etc.).  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 \<Exemples de chemin d’accès > \AdaptersUsage\MSMQLarge  
  
> [!NOTE]
>  Si vous utilisez une version 64 bits de Windows et [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], l’exemple est installé dans le **(x86) de C:\Program Files \Microsoft BizTalk Server \<version > \SDK\Samples\AdaptersUsage\MSMQLarge** dossier.  Notez cette modification pour toutes les autres instructions dans ce document à l’aide de la **C:\Program Files** dossier.  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|**Fichier**|**Description**|  
|--------------|---------------------|  
|**MQRTLarge.dll**|Fournit un composant additionnel pour Message Queuing en mode natif. Expose les **MQSendLargeMessage** et **MQReceiveLargeMessage** API.<br /><br /> Vous devez installer [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] sur une version 64 bits de Windows pour pouvoir accéder à la version 64 bits de MQRTLarge.dll.<br /><br /> Pour une solution MSMQ sans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], MQRTLarge.dll peut toujours fonctionner correctement. Toutefois, cette configuration n’est pas recommandée qui prend en charge de Microsoft et des résultats inattendus peuvent se produire si utilisé en dehors de la [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] environnement.|  
|||  
|**LargeMessages.sln**|Fournit une solution [!INCLUDE[vs2010](../includes/vs2010-md.md)] pour créer l'exécutable SendLargeMessage utilisé dans l'exemple.|  
|**XMLCreator.sln**|Fournit une solution [!INCLUDE[vs2010](../includes/vs2010-md.md)] pour créer l'exécutable XMLCreator qui génère un fichier .xml de test pour l'exemple de SDK.|  
  
## <a name="configuring-biztalk-server-and-creating-the-msmq-queue"></a>Configuration de BizTalk Server et création de la file d'attente MSMQ  
 Vérifiez que vous avez installé [!INCLUDE[vs2010](../includes/vs2010-md.md)], Microsoft Message Queuing et [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
#### <a name="to-configure-biztalk-server"></a>Pour configurer BizTalk Server  
  
1.  Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], ouvrez le **C:\Program Files\Microsoft BizTalk Server \<version > \SDK\Samples\AdaptersUsage\MSMQLarge\LargeMessages.sln** fichier solution.  Générez l'exemple.  
  
2.  Créer un **C:\Demo** répertoire où [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] placera les messages de MSMQ.  
  
3.  Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
4.  Créez un port d'envoi pour que l'exemple puisse écrire le message.  
  
    -   Développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, avec le bouton droit **Ports d’envoi**, cliquez sur **New**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
5.  Dans le **statique propriétés du Port d’envoi unidirectionnel** boîte de dialogue, définissez le nom du port sur **MySendPort**.  
  
6.  Définissez le type de transport sur **fichier**.  
  
7.  Cliquez sur le **configurer** bouton pour ouvrir la **propriétés du Transport File** formulaire. Entrez **C:\Demo** dans **dossier de Destination**. Vérifiez que l'identité de l'instance d'hôte a accès au dossier C:\Demo.  
  
8.  Vérifiez que **nom de fichier** a la valeur **%MessageID%.xml**. Cliquez sur **OK**.  
  
9. Cliquez sur **Filtres**.  
  
    1.  Définissez **propriété** à **BTS. ReceivePortName**.  
  
    2.  Définissez **opérateur** à  **=** .  
  
    3.  Définissez **valeur** à **MyReceivePort**.  
  
    4.  Cliquez sur **OK**.  
  
10. Créez un port de réception pour accepter le message de MSMQ.  
  
    1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez sur **Ports de réception**.  
  
    2.  Cliquez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.  
  
11. Dans le **propriétés du Port de réception** boîte de dialogue, définissez le nom du port sur **MyReceivePort**, puis cliquez sur **OK**.  
  
12. Après la création d'un port de réception pour l'exemple, vous devez créer un emplacement de réception.  
  
    1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez sur **emplacements de réception**.  
  
    2.  Cliquez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.  
  
    3.  Définir le nom de l’emplacement de réception à **MSMQReceiveLocation**.  
  
    4.  Dans le **sélectionner un Port de réception** boîte de dialogue, sélectionnez **MyReceivePort**.  
  
    5.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue, définissez **Type de Transport** à **MSMQ**.  
  
    6.  Dans le **adresse (URI)** , cliquez sur **configurer** pour ouvrir le **propriétés du Transport MSMQ** formulaire. Définissez **file d’attente** à **localhost\private$ \test**.  
  
    7.  Définissez **transactionnel** à `True`, puis cliquez sur **OK**.  
  
13. Vous devez rendre les ports et les emplacements de réception disponibles pour les utiliser via la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
    1.  Avec le bouton droit **MySendPort**, puis cliquez sur **Enlist**.  
  
    2.  Avec le bouton droit **MySendPort**, puis cliquez sur **Démarrer**.  
  
    3.  Avec le bouton droit **MSMQReceiveLocation**, puis cliquez sur **activer**.  
  
#### <a name="to-create-the-msmq-queue-in-windows-server-2008-r2-or-windows-server-2008-sp2"></a>Pour créer la file d'attente MSMQ sous Windows Server 2008 R2 ou Windows Server 2008 SP2  
  
1.  Cliquez sur **Démarrer**, avec le bouton droit **ordinateur**, puis cliquez sur **gérer**.  
  
2.  Développez le **fonctionnalités** nœud.  
  
3.  Développez le **Message Queuing** nœud.  
  
4.  Cliquez sur le **files d’attente privées** nœud, cliquez sur **nouveau**, puis cliquez sur **file d’attente privée**.  
  
5.  Sous **nom de la file d’attente**, entrez **test**. Vérifiez que le **transactionnel** case à cocher est activée.  
  
6.  Cliquez sur **OK**.  
  
#### <a name="to-create-the-msmq-queue-in-windows-7-or-windows-vista-sp2"></a>Pour créer la file d'attente MSMQ sous Windows 7 ou Windows Vista SP2  
  
1.  Cliquez sur **Démarrer**, avec le bouton droit **ordinateur**, puis cliquez sur **gérer**.  
  
2.  Développez **Services et Applications**, puis développez le **Message Queuing** nœud.  
  
    > [!NOTE]
    >  Si **Message Queuing** n’est pas installé sur l’ordinateur, accédez à **le panneau de configuration > Programmes > Programmes et fonctionnalités**, puis sélectionnez **ou désactiver des fonctionnalités Windows d’activer**. Vérifiez toutes les fonctionnalités sous **Microsoft Message Queue (MSMQ) Server**, puis cliquez sur **OK**.  
  
3.  Cliquez sur le **files d’attente privées** nœud, cliquez sur **nouveau**, puis cliquez sur **file d’attente privée**.  
  
4.  Sous **nom de la file d’attente**, entrez **test**. Vérifiez que le **transactionnel** case à cocher est activée.  
  
5.  Cliquez sur **OK**.  
  
## <a name="creating-a-test-file-and-running-the-sample"></a>Création d'un fichier de test et exécution de l'exemple  
  
#### <a name="to-create-a-large-test-file"></a>Pour créer un fichier de test volumineux  
  
1.  Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], ouvrez la solution **C:\Program Files\Microsoft BizTalk Server \<version > \SDK\Samples\AdaptersUsage\MSMQLarge\XMLCreator\XMLCreator.sln**.  
  
2.  Générez et exécutez le projet.  
  
3.  Sous **corps XML**, type **il s’agit d’un message de test**.  
  
4.  Sous **nombre de tentatives de copie du corps XML**, type `250000`.  
  
5.  Sous **emplacement du fichier XML**, type `C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\AdaptersUsage\MSMQLarge\LargeFile.xml`.  
  
6.  Cliquez sur **créer XML**, puis cliquez sur **OK**.  
  
#### <a name="to-run-the-sample"></a>Pour exécuter l’exemple  
  
1.  Ouvrez une invite de commandes et accédez au répertoire **C:\Program Files\Microsoft BizTalk Server \<version > \SDK\Samples\AdaptersUsage\MSMQLarge\SendLargeMessage\bin\debug**.  
  
2.  À l’invite de commandes, exécutez **SendLargeMessage.exe**. L’exécutable SendLargeMessage accepte deux variables. La première correspond à l’emplacement de la file d’attente MSMQ et la seconde à l’emplacement du fichier .xml à envoyer :  
  
    ```  
    DIRECT=OS:localhost\private$\Test  "C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\AdaptersUsage\MSMQLarge\LargeFile.xml"  
    ```  
  
3.  Vérifiez qu’un fichier de la même taille a été créé sur le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] ordinateur dans le **C:\Demo** active. Il s'agit du répertoire identifié dans le port d'envoi MySendPort.  
  
## <a name="comments"></a>Commentaires  
 SendLargeMessage.exe référence le **LargeMessages** API, qui à son tour fait référence à la BizTalk Message Queuing Extension de messages volumineux (MQRTLarge.dll) API. L'API Extension de messages volumineux Message Queuing est un composant additionnel pour Message Queuing en mode natif qui permet le traitement des messages de plus de 4 Mo.  
  
 Cet exemple utilise le **MQSendLargeMessage** et l’expose l’API du .NET Framework à l’aide de la **LargeMessages** API.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension de messages volumineux Message Queuing BizTalk](../core/biztalk-message-queuing-large-message-extension.md)   
 [Exemples d’adaptateurs - utilisation](../core/adapter-samples-usage.md)