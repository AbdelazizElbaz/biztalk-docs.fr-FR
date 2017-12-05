---
title: SendMSMQMessage | Documents Microsoft
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
ms.assetid: 398bc396-0c66-4d55-886a-0d9bdab6476f
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a48cbb333a724d2f60141f0f67ef3feccb1d3954
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="sendmsmqmessage"></a>SendMSMQMessage
L'exemple SendMSMQMessage montre comment envoyer un message à un port MSMQ à partir d'une application basée sur .NET. Il fournit également des instructions sur la façon de configurer Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à utiliser un MSMQ emplacement de réception.  
  
 Vous devez être conscient que de nombreuses opérations dans Message Queuing sont asynchrones. Que de nombreux appels d’API de MSMQ (par exemple, **System.Messaging.MessageQueue.Send**) retour à l’appelant avant l’opération demandée soit entièrement terminée. MSMQ intègre un mécanisme qui renvoie des commentaires à l'application une fois l'opération terminée. Ce mécanisme inclut l'utilisation d'une file d'administration. MSMQ renvoie des commentaires sous forme de messages dans la file d'administration. La file d'administration à laquelle MSMQ renvoie des commentaires est spécifiée lors de l'appel de l'API MSMQ. Ainsi, par exemple, lors de l’envoi d’un message à l’aide de la **System.Messaging.MessageQueue.Send** API, l’application peut spécifier le nom de la file d’administration à l’aide de la **PROPID_M_ADMIN_QUEUE** message, propriété sur le message passé dans l’appel à **System.Messaging.MessageQueue.Send**. Même si l’application peut obtenir un code de retour réussi le **System.Messaging.MessageQueue.Send** appel, si le message d’opération d’envoi échoue, par la suite MSMQ écrit un message à cet effet dans la file d’attente d’administration spécifié. Si l'application ne spécifie pas de file d'administration, l'échec d'envoi entraîne la perte du message sans aucun diagnostic. Le message disparaît purement et simplement. Il existe un numéro d’erreur à envoyer des situations dans MSMQ qui peut entraîner cette situation, par exemple, faire non transactionnel à une file d’attente transactionnelle.  
  
 Dans le cadre de cet exemple, il est important que le code spécifie un type de transaction dans l’appel à **System.Messaging.MessageQueue.Send** qui soit cohérent avec la prise en charge de la transaction spécifiée pour la file d’attente à laquelle le message est envoyé. Si ce n'est pas le cas et si aucune file d'administration n'est spécifiée (comme dans cet exemple), l'API MSMQ écarte le message envoyé sans le signaler (aucun code d'erreur n'est renvoyé à l'application, aucun diagnostic n'est écrit dans le journal des événements, etc.).  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 \<Exemples de chemin d’accès\>\AdaptersUsage\SendMSMQMessage\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichiers| Description|  
|-----------|-----------------|  
|App.ico, AssemblyInfo.cs, SendMSMQMessage.csproj, SendMSMQMessage.sln|Fournir un projet, une solution et des fichiers connexes pour l'application graphique destinée à cet exemple.|  
|Form1.cs, Form1.resx|Fournir une source Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] .NET et des fichiers de formulaires pour l'application graphique destinée à cet exemple.|  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
 Vous pouvez utiliser le code de l'application graphique simple incluse dans cet exemple pour comprendre comment envoyer des messages aux emplacements de réception MSMQ à l'intérieur de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à partir d'application compatibles .NET telles que Microsoft Office, de pages ASP.NET, etc.  
  
## <a name="building-and-initializing-the-sample"></a>Création et initialisation de l'exemple  
  
#### <a name="to-build-the-sample-executable"></a>Pour créer l'exécutable de l'exemple  
  
1.  À l'aide de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le fichier de solution SendMSMQMessage.sln.  
  
2.  Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
## <a name="configuring-biztalk-server-and-creating-the-msmq-queue"></a>Configuration de BizTalk Server et création de la file d'attente MSMQ  
 Les procédures suivantes permettent de configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et de créer la file d'attente MSMQ pour l'exécution de l'exemple.  
  
#### <a name="to-create-the-msmq-queue-in-windows-server-2008-r2-or-windows-server-2008-sp2"></a>Pour créer la file d'attente MSMQ sous Windows Server 2008 R2 ou Windows Server 2008 SP2  
  
1.  Cliquez sur **Démarrer**, avec le bouton droit **ordinateur**, puis cliquez sur **gérer**.  
  
2.  Développez le **fonctionnalités** nœud.  Si **Message Queuing** est ne pas installé, cliquez sur **fonctionnalités** et sélectionnez **ajouter des fonctionnalités**.  Vérifiez **Message Queuing**, cliquez sur **suivant**, puis cliquez sur **installer** pour installer MSMQ sur ce système.  
  
3.  Développez le **Message Queuing** nœud.  
  
4.  Cliquez sur le **files d’attente privées** nœud, cliquez sur **nouveau**, puis cliquez sur **file d’attente privée**.  
  
5.  Sous **nom de la file d’attente**, entrez `test`. Vérifiez que le **transactionnel** case à cocher est activée.  
  
6.  Cliquez sur **OK**.  
  
#### <a name="to-create-the-msmq-queue-in-windows-7-or-windows-vista-sp2"></a>Pour créer la file d'attente MSMQ sous Windows 7 ou Windows Vista SP2  
  
1.  Cliquez sur **Démarrer**, avec le bouton droit **ordinateur**, puis cliquez sur **gérer**.  
  
2.  Développez **Services et Applications**, puis développez le **Message Queuing** nœud.  
  
    > [!NOTE]
    >  Si **Message Queuing** n’est pas installé sur l’ordinateur, accédez à **le panneau de configuration > Programmes > Programmes et fonctionnalités**, puis sélectionnez **ou désactiver des fonctionnalités Windows d’activer**. Vérifiez toutes les fonctionnalités sous **Microsoft Message Queue (MSMQ) Server**, puis cliquez sur **OK**.  
  
3.  Cliquez sur le **files d’attente privées** nœud, cliquez sur **nouveau**, puis cliquez sur **file d’attente privée**.  
  
4.  Sous **nom de la file d’attente**, entrez **test**. Vérifiez que le **transactionnel** case à cocher est activée.  
  
5.  Cliquez sur **OK**.  
  
#### <a name="to-configure-biztalk-server"></a>Pour configurer BizTalk Server  
  
1.  Sélectionnez le dossier dans lequel vous voulez recevoir les messages. Les étapes suivantes sont basées sur l'hypothèse que vous avez sélectionné le dossier C:\Demo\Report, mais vous pouvez les ajuster si nécessaire pour un autre dossier.  
  
2.  Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
3.  Créer une application nommée **MSMQSample**.  
  
4.  Avec le bouton droit **Ports de réception**, cliquez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.  
  
5.  Dans le **propriétés du Port de réception** boîte de dialogue le **nom** , saisissez **MyReceivePort**, puis cliquez sur **OK**.  
  
6.  Avec le bouton droit **emplacements de réception**, cliquez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**. Dans le **sélectionner un Port de réception** boîte de dialogue, sélectionnez le port que vous venez créée, cliquez sur **OK**.  
  
7.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** , tapez un nom pour le port de réception, tel que **MSMQReceiveLocation**.  
  
8.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue, pour le type de transport, sélectionnez **MSMQ** .  
  
9. Cliquez sur **configurer** pour ouvrir le **propriétés du Transport MSMQ** boîte de dialogue. Définissez **file d’attente** à `localhost\private$\test`, définissez **transactionnel** à `True`, puis cliquez sur **OK**.  
  
10. Développez l’application, sélectionnez **Ports d’envoi**, sélectionnez **nouveau**, sélectionnez **Port d’envoi unidirectionnel statique**.  
  
11. Dans le **propriétés de Port d’envoi** boîte de dialogue le **nom** , tapez un nom pour le port d’envoi, tel que **MySendPort**.  
  
12. Définir le **Type de Transport** propriété **fichier**.  
  
13. Cliquez sur **configurer** pour ouvrir le **propriétés du Transport File** boîte de dialogue.  
  
14. Dans le **propriétés du Transport FILE** boîte de dialogue, définissez la **dossier de Destination** propriété **C:\Demo\Report**, conservez les paramètres par défaut pour les autres propriétés, puis Cliquez sur **OK**.  
  
15. Sélectionnez **filtres**, puis ajoutez une nouvelle ligne en définissant **propriété** à **BTS. ReceivePortName**. Laisser la **opérateur** colonne définie sur  **==** , définissez le **valeur** colonne **MyReceivePort**, puis cliquez sur **OK**.  
  
16. Avec le bouton de votre nouveau port d’envoi, puis cliquez sur **Enlist**.  
  
17. Avec le bouton de votre nouveau port d’envoi à nouveau, puis cliquez sur **Démarrer**.  
  
18. Avec le bouton de votre nouvel emplacement de réception, puis cliquez sur **activer**.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]est maintenant prêt à utiliser avec cet exemple.  
  
## <a name="running-the-sample"></a>Exécution de l’exemple  
 La procédure suivante permet d'exécuter l'exemple SendMSMQMessage.  
  
#### <a name="to-run-the-sample"></a>Pour exécuter l’exemple  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<Exemples de chemin d’accès\>\AdaptersUsage\SendMSMQMessage\bin\Debug  
  
2.  Exécutez le fichier SendMSMQMessage.exe qui démarre l'application graphique qui fournit l'interface utilisateur pour cet exemple.  
  
3.  Dans l’application graphique, dans le **nom de l’ordinateur BizTalk** , tapez le nom de l’ordinateur local.  
  
4.  Essayez du **envoyer encapsulé** option :  
  
    1.  Vous pouvez également modifier le texte dans le **corps du Message** boîte.  
  
    2.  Cliquez sur **envoyer encapsulé**.  
  
     Si l'opération réussit, vous voyez ce qui suit :  
  
    -   Le mot **réussite** apparaît en rouge dans la zone juste au-dessus des boutons.  
  
    -   Un fichier apparaît dans le dossier de destination, C:\Demo\Reports. Ce fichier contient le texte à partir de la **corps du Message** encapsulé dans des balises XML simples par la bibliothèque de files d’attente de message .NET.  
  
     Si l'opération échoue, un message d'erreur s'affiche juste au-dessus des boutons.  
  
5.  Essayez du **envoyer Exact** option :  
  
    1.  Vous pouvez également modifier le texte dans le **corps du Message** boîte.  
  
    2.  Cliquez sur **envoyer exact**.  
  
     Si l'opération réussit, vous voyez ce qui suit :  
  
    -   Le mot **réussite** apparaît en rouge dans la zone juste au-dessus des boutons.  
  
    -   Un fichier apparaît dans le dossier de destination, C:\Demo\Reports. Ce fichier contient le texte à partir de la **corps du Message** exactement tel qu’il apparaît dans la zone de texte.  
  
     Si l'opération échoue, un message d'erreur s'affiche juste au-dessus des boutons.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’adaptateurs- Utilisation](../core/adapter-samples-usage.md)