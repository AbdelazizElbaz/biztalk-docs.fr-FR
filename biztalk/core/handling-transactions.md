---
title: La gestion des Transactions | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d360742-e969-4651-b364-9edc6a93b8d4
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 954d0e91e078c7f973bddc22961c760aa4080941
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="handling-transactions"></a>La gestion des Transactions
## <a name="transacted-receivers"></a>Récepteurs traités  
 La principale différence entre les récepteurs traités et les récepteurs non traités est que les récepteurs traités créent et utilisent une transaction MSDTC explicite pour assurer l'atomicité entre la source de données et la base de données MessageBox de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. En général, les autres aspects de l'adaptateur sont les mêmes.  
  
 Notez que l'adaptateur de réception requête-réponse n'utilise une transaction que pour envoyer le message de requête original au moteur de messagerie. Une transaction différente est nécessaire pour la transmission de la réponse envoyée du moteur de messagerie à l'adaptateur. Cela est dû au fait que l'étendue de la première transaction va de l'adaptateur à la base de données MessageBox. Le message de requête suivant n'est pas envoyé à l'adaptateur depuis le moteur de messagerie avant que la transaction du message de requête original n'ait été validée.  
  
 Le diagramme d'interaction d'objets suivant présente l'interaction entre l'adaptateur et le moteur de messagerie pendant l'envoi transactionnel des messages entrants. Dans cet exemple, la série d'interactions suivante se produit :  
  
1.  L'adaptateur reçoit un nouveau lot du moteur.  
  
2.  L'adaptateur crée et retourne une nouvelle transaction MSDTC.  
  
3.  L'adaptateur procède à une lecture destructive depuis la source de données inscrite dans la transaction.  
  
4.  L'adaptateur envoie le message.  
  
5.  L’adaptateur appelle la méthode **fait** sur le lot, en transmettant sa transaction MSDTC et son **BatchComplete** pointeur de rappel. Le moteur retourne un **IBTDTCCommitConfirm** interface.  
  
6.  Le moteur traite le lot, rappelle l’adaptateur sur son **BatchComplete** implémentation et transmet l’état du traitement des messages à l’adaptateur.  
  
7.  Si le lot a réussi l’adaptateur valide la transaction et appelle le **IBTDTCCommitConfirm.DTCCommitConfirm** API avec un `true` indiquant la validation de valeur.  
  
 ![](../core/media/transactedreceiver.gif "TransactedReceiver")  
  
## <a name="transacted-transmitters"></a>Émetteurs traités  
 Les adaptateurs traités sont pour la plupart très similaires aux adaptateurs non traités. La principale différence réside dans le fait que l'adaptateur traité envoie les données du message vers une ressource inscrite dans une transaction MSDTC.  
  
 **Conseil pour l’implémentation :** pour les envois, l’adaptateur doit utiliser la même transaction MSDTC pour écrire des données vers la destination et pour les supprimer via le **IBTTransportBatch.DeleteMessage** appel de méthode. Seules ces deux opérations doivent être traitées. Toutes les autres opérations, telles que **IBTTransportBatch.Resubmit**, **IBTTransportBatch.MoveToNextTransport**, et **IBTTransportBatch.MoveToSuspendQ** ne doivent pas nécessairement être avec transaction. Cela est dû au fait que le moteur utilise implicitement une transaction et que ces types d'opérations n'ont pas besoin d'être atomiques par rapport à la destination.  
  
 Le diagramme d'interaction d'objets suivant présente les interactions entre l'adaptateur et le moteur. La séquence des événements se déroule comme suit :  
  
1.  Le moteur reçoit un nouveau lot de l'adaptateur.  
  
2.  Le moteur ajoute deux messages au nouveau lot.  
  
3.  Le moteur appelle **fait** sur le lot, à l’origine de l’adaptateur valider le lot à sa file d’attente de transmission interne servie par sa réserve de threads.  
  
4.  L'adaptateur crée et retourne une nouvelle transaction MSDTC.  
  
5.  L'adaptateur transmet les messages en inscrivant la destination dans la transaction MSDTC. Par exemple, en l'écrivant dans une base de données [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
6.  Après la transmission, l'adaptateur reçoit un nouveau lot du moteur.  
  
7.  L’adaptateur appelle la méthode **DeleteMessage** pour les messages qu’il a été transmis avec succès.  
  
8.  L’adaptateur appelle la méthode **fait** sur le lot en transmettant sa transaction DTC. Le moteur retourne un **IBTDTCCommitConfirm** interface.  
  
9. Le moteur traite le lot et supprime les messages de la file d'attente de l'application.  
  
10. Le moteur rappelle l’adaptateur **IBTBatchCallback** interface avec des informations sur la réussite de ses opérations de suppression.  
  
11. Si le lot a été correctement traité, l'adaptateur valide les transactions.  
  
12. L’adaptateur appelle la méthode **IBTDTCCommitConfirm.DTCCommitConfirm** pour informer le moteur que la transaction a été correctement validée.  
  
 ![](../core/media/transactedtransmitter.gif "Transactedtransmitter")  
  
### <a name="transacted-solicit-response-adapters"></a>Adaptateurs de sollicitation-réponse traités  
 À la différence des réceptions bidirectionnelles, les envois bidirectionnels peuvent être réalisés à l'aide de la même transaction DTC. Adaptateurs de sollicitation-réponse traités doivent utiliser le même **IBTTransportBatch** pour le **SubmitResponseMessage** et **DeleteMessage** operations. Ce lot doit utiliser la même transaction MSDTC utilisée pour envoyer et recevoir la paire de messages de sollicitation-réponse. Il s'agit de garantir l'atomicité de l'échange des messages de sollicitation-réponse.  
  
## <a name="service-components-and-byot"></a>Composants de service et BYOT  
 Les API du moteur de messagerie requièrent l'utilisation d'une transaction MSDTC. Cependant, certains composants .NET sont conçus pour être utilisés en tant que composants pris en charge et ne permettent pas la validation ou l'abandon programmés de la transaction. À la place, la transaction est automatiquement validée par COM+ Runtime sur cette plateforme.  
  
 Dans ces scénarios, l'adaptateur doit utiliser Bring Your Own Transaction (BYOT). Cela permet à l'adaptateur de créer une transaction MSDTC, d'instancier le composant .NET qui utilise la transaction, et permet à ce composant d'hériter de la transaction créée plutôt que d'avoir à en créer une. Le .NET Framework fournit **System.EnterpriseServices.BYOT** à cet effet. Le Kit de développement logiciel BaseAdapter fournit une classe d’assistance, **BYOTTransaction**, à cet effet.  
  
## <a name="avoiding-race-conditions"></a>Prévention des conditions d'engorgement  
 Lorsque vous écrivez le code d'un adaptateur qui crée un objet transactionnel et le remet à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous prenez la responsabilité que le code :  
  
-   résout les erreurs dans les messages associés au lot ;  
  
-   décide de l'issue finale de la transaction associée à l'opération de traitement par lot.  
  
 L'adaptateur doit informer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] du résultat final de la transaction pour pouvoir tenir à jour ses données de suivi internes. L’adaptateur informe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] du résultat final en appelant **DTCConfirmCommit**. S'il ne le fait pas, une fuite de mémoire sensible se produit.  
  
 Les deux tâches que sont la résolution des erreurs et la décision concernant le résultat final (indiquées ci-dessus) d'un lot envoyé sont en apparence assez simples. En fait, elles s'appuient sur des informations provenant de plusieurs threads :  
  
-   L’adaptateur traite les erreurs basées sur les informations passées par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à la **BatchComplete** rappel dans l’adaptateur. Ce rappel est sur le thread de l’adaptateur.  
  
-   **DTCConfirmCommit** est une méthode de la **IBTDTCCommitConfirm** objet. Une instance de la **IBTDTCCommitConfirm** est retourné par le lot **IBTTransportBatch::Done** appeler. Cette instance est sur le même thread que le **IBTTransportBatch::Done** appeler, lequel est différent du thread de l’adaptateur.  
  
-   Pour chaque appel que l’adaptateur effectue vers **IBTTransportBatch::Done** il y a un rappel correspondant, **BatchComplete**, qui est appelée par le moteur de messagerie dans un thread distinct pour signaler le résultat de l’envoi du lot. Dans **BatchComplete** l’adaptateur doit valider ou annuler la transaction selon que le lot ayant réussi ou échoué. Dans les deux cas, l’adaptateur doit appeler **DTCConfirmCommit** pour signaler l’état de la transaction au moteur de messagerie.  
  
 Il existe une condition d’engorgement possible car implémentation de l’adaptateur de **BatchComplete** peut supposer que le **IBTDTCCommitConfirm** objet retourné par **IBTTransportBatch::Done** est toujours disponible lorsque **BatchComplete** s’exécute. Toutefois, **BatchComplete** peut être appelée dans un thread séparé de moteur de messagerie, avant même que **IBTTransportBatch::Done** retourne. Il est possible de que lorsque l’adaptateur tente d’accéder à la **IBTDTCCommitConfirm** objet dans le cadre de la **BatchComplete** implémentation, il existe une violation d’accès.  
  
 Le problème est résolu avec un événement dans l’exemple suivant. Ici, le pointeur d'interface fait l'objet d'un accès par l'intermédiaire d'une propriété qui fait appel à un événement. La méthode get attend toujours que la méthode set soit terminée.  
  
```  
protected IBTDTCCommitConfirm CommitConfirm  
{  
   set  
   {  
       this.commitConfirm = value;  
       this.commitConfirmEvent.Set();  
   }  
   get  
   {  
       this.commitConfirmEvent.WaitOne();  
       return this.commitConfirm;  
   }  
}  
protected IBTDTCCommitConfirm commitConfirm = null;  
private ManualResetEvent commitConfirmEvent = new ManualResetEvent(false);  
```  
  
 Désormais affecter la valeur de retour à partir de **IBTTransportBatch::Done** à cette propriété et l’utiliser dans le **BatchComplete** appeler.  
  
## <a name="see-also"></a>Voir aussi  
 [Lots de messages transactionnels](../core/transactional-message-batches.md)