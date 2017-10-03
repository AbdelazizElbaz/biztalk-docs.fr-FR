---
title: "Traitement par lot des Messages pour le traitement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 32bf0b70-e9d1-4fab-9c74-160e51390700
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef14179c1af460afc516b7fa331ee30a758219c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="batching-messages-for-receive-processing"></a>Traitement par lot des messages pour le traitement de réception
## <a name="batch-callbacks"></a>Rappels en lot  
 Les lots envoyés par les adaptateurs de réception au moteur de messagerie étant traités de façon asynchrone, l'adaptateur a besoin d'un mécanisme pour lier un rappel à un état quelconque au sein de l'adaptateur afin de pouvoir être notifié du succès ou de l'échec de l'opération et réaliser les actions de nettoyage nécessaires. La sémantique des rappels étant souple, les adaptateurs peuvent utiliser une des trois approches possibles ou les combiner. Il s'agit des paramètres suivants :  
  
-   Tous les rappels sont effectuées sur la même instance d’objet qui implémente **IBTBatchCallBack**.  
  
-   Le cookie passé au moteur au moment où une requête de nouveau lot est effectuée est utilisé pour mettre le rappel en corrélation avec l'état au sein des adaptateurs.  
  
-   Il existe un objet de rappel différent pour chaque lot qui implémente **IBTBatchCallBack**. Ici, chaque objet détient son propre état privé.  
  
 Lorsque le lot a été traité, l’adaptateur est rappelé sur son implémentation de **IBTBatchCallBack.BatchComplete**. C'est le premier paramètre qui indique l'état global du lot, à savoir le paramètre HRESULT. Si la valeur de ce paramètre est supérieure ou égale à zéro, le lot a correctement été traité dans la mesure où le moteur devient propriétaire des données et où l'adaptateur est libre de supprimer ces données du câble. Un état négatif indique que le lot a échoué : aucune des opérations du lot ont réussi et que l’adaptateur est responsable de la gestion de l’échec.  
  
 Si le lot a échoué, l'adaptateur a besoin de savoir quel élément de quelle opération a échoué. Supposons, par exemple, que l'adaptateur était en train de lire 20 fichiers provenant du disque et de les envoyer en un seul lot vers [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Si le dixième fichier a été endommagé, la carte doit suspendre qu’un fichier et de renvoyer les 19 restants. Ces informations sont disponibles à l’adaptateur dans les deuxième et troisième paramètres :`opCount` (nombre d’opérations) de type short et `operationStatus`, qui est de type BTBatchOperationStatus [].  
  
> [!NOTE]
>  Au sein d'un même objet de lot, un message ne doit jamais être envoyé plus d'une fois, au risque de provoquer des erreurs au niveau du moteur.  
  
 Le nombre d’opérations indique combien de types d’opérations dans le lot (la taille de la **BTBatchOperationStatus** tableau). Chaque élément du tableau d'état des opérations correspond à un type d'opération donné. À l’aide de la **BTBatchOperationStatus** tableau, l’adaptateur peut déterminer quel élément d’une opération donnée a échoué en consultant le **BTBatchOperationStatus.MessageStatus** tableau pour HRESULT négatif valeurs indiquant l’échec. Dans le scénario ci-dessus, l'adaptateur crée un nouveau lot qui contient 19 envois de message et un message suspendu.  
  
 Le fragment de code ci-dessous montre comment l'adaptateur demande un nouveau lot auprès du moteur par l'intermédiaire de son proxy de transport et envoie un seul message au moteur à l'aide de l'approche par cookie. Le moteur de messagerie appelle la **BatchComplete** le rappel de lot lorsqu’il a terminé le traitement de la totalité du traitement de la méthode de messages envoyés.  
  
```  
using Microsoft.BizTalk.TransportProxy.Interop;  
using Microsoft.BizTalk.Message.Interop;  
  
public class MyAdapter :   
                  IBTTransport,   
                  IBTTransportConfig,   
                  IBTTransportControl,  
                  IPersistPropertyBag,   
                  IBaseComponent,  
                  IBTBatchCallBack  
{  
      private IBTTransportProxy _tp;  
  
      public void BatchComplete(      
            Int32                         status,   
            Int16                         opCount,   
            BTBatchOperationStatus[]      operationStatus,   
            System.Object                 callbackCookie)  
      {  
            // Use cookie to correlate callback with work done,  
            // in this example the batch is to submit a single  
            // file the name of which will be in the  
            // callbackCookie  
            string fileName = (string)callbackCookie;  
            if ( status >= 0 )  
                  // DeleteFile from disc  
                  File.Delete(fileName);          
            else  
                  // Rename file to fileName.bad  
                  File.Move(fileName, fileName + ".bad");  
      }  
  
      private void SubmitMessage(  
            IBaseMessage                  msg,   
            string                        fileName)  
      {  
            // Note: Pass in the filename as the cookie  
            IBTTransportBatch batch =   
                  _tp.GetBatch(this, (object)fileName);  
  
            // Add msg to batch for submitting   
            batch.SubmitMessage(msg);   
  
            // Process this batch  
            batch.Done(null);  
      }  
}  
```  
  
 Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] kit SDK inclut des exemples pour les adaptateurs suivants : fichier, HTTP, MSMQ et l’adaptateur transactionnel. Tous ces adaptateurs reposent sur un bloc de construction commun appelé BaseAdapter. La version 1.0.1 de BaseAdapter inclut tout le code nécessaire à l'analyse de l'état des opérations et à la régénération des nouveaux lots à envoyer.  
  
## <a name="race-condition"></a>Condition d'engorgement  
 Les deux tâches que sont la résolution des erreurs et la décision concernant le résultat final d'un lot envoyé sont en apparence assez simples. En fait, elles s'appuient sur des informations provenant de plusieurs threads :  
  
-   L’adaptateur traite les erreurs basées sur les informations passées par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l’adaptateur **BatchComplete** méthode de rappel. Ce rappel s'exécute sur le thread de l'adaptateur.  
  
-   **DTCCommitConfirm** est une méthode de la **IBTDTCCommitConfirm** objet. Une instance de la **IBTDTCCommitConfirm** est retourné par le lot **IBTTransportBatch::Done** appeler. Cette instance est sur le même thread que le **IBTTransportBatch::Done** appeler, lequel est différent du thread de rappel de l’adaptateur.  
  
 Pour chaque appel que l’adaptateur effectue vers **IBTTransportBatch::Done** le moteur de messagerie effectue un appel correspondant à la méthode de rappel **BatchComplete** dans un thread distinct pour signaler le résultat de la envoi du lot. Dans **BatchComplete** l’adaptateur doit valider ou annuler la transaction selon que le lot ayant réussi ou échoué. Dans les deux cas, l’adaptateur doit appeler **DTCCommitConfirm** pour signaler l’état de la transaction.  
  
 Il existe une condition d’engorgement possible car implémentation de l’adaptateur de **BatchComplete** peut supposer que le **IBTDTCCommitConfirm** objet retourné par **IBTTransportBatch::Done** est toujours disponible lorsque **BatchComplete** s’exécute. Toutefois, **BatchComplete** peut être appelée dans un thread séparé de moteur de messagerie, avant même que **IBTTransportBatch::Done** retourne. Il est possible de qui lorsque l’adaptateur tente d’accéder à la **IBTDTCCommitConfirm** objet dans le cadre de la **BatchComplete** implémentation, ici, est une violation d’accès parce que l’appel de thread n’est plus Il existe. Utilisez la solution suivante pour éviter cette condition.  
  
 L'exemple suivant permet de résoudre le problème à l'aide d'un événement. Ici, le pointeur d'interface fait l'objet d'un accès par l'intermédiaire d'une propriété qui fait appel à un événement. La méthode get attend toujours que la méthode set soit terminée avant de poursuivre.  
  
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
  
## <a name="batch-status-codes"></a>Codes d'état des lots  
 Le code d'état global du lot indique le résultat du lot. L'état de l'opération donne le code d'état de l'envoi pour chaque élément de message. Les lots peuvent échouer pour diverses raisons. Une erreur liée à la sécurité peut se produire ou le message peut avoir été envoyé au moment où le moteur était en cours d'arrêt. (Généralement, lorsque le moteur s'arrête, il n'accepte pas de nouvelle tâche mais permet aux tâches in-process de se terminer.) Le tableau suivant répertorie certaines valeurs courantes du paramètre HRESULT renvoyées soit dans l'état du lot, soit dans l'état de l'opération. Il indique également s'il s'agit d'un code de réussite ou d'échec. La manipulation de ces codes est décrite plus en détail dans [comment gérer les défaillances d’adaptateur](../core/how-to-handle-adapter-failures.md).  
  
|Code (défini dans la classe BTTransportProxy)|Code de réussite/d'échec| Description|  
|----------------------------------------------------|---------------------------|-----------------|  
|BTS_S_EPM_SECURITY_CHECK_FAILED|Réussi|Le port a été configuré pour effectuer une vérification de sécurité et supprimer les messages dont l'authentification a échoué. Les adaptateurs ne devraient pas suspendre les lots qui renvoient ce code d'état.|  
|BTS_S_EPM_MESSAGE_SUSPENDED|Réussi|Indique qu'un ou que plusieurs messages ont été suspendus et que le moteur est propriétaire des données. Il s'agit d'un code de réussite dans la mesure où le moteur de messagerie a accepté les messages envoyés.|  
|E_BTS_URL_DISALLOWED|Failure|Un message a été envoyé avec un non valide **InboundTransportLocation**.|  
  
## <a name="batch-operations"></a>Opérations de traitement par lot  
 Le tableau suivant répertorie les méthodes membres et les opérations de la **IBTTransportBatch** de l’objet que l’adaptateur utilise pour ajouter des tâches à un lot donné.  
  
|Nom de la méthode|Type d'opération| Description|  
|-----------------|--------------------|-----------------|  
|**SubmitMessage**|Envoyer|Envoie un message au moteur.|  
|**SubmitResponseMessage**|Envoyer|Envoie un message de réponse au moteur. Il s'agit d'un message de réponse d'une paire sollicitation-réponse.|  
|**DeleteMessage**|DELETE|Supprime un message qu'un adaptateur a correctement transmis sur le câble à l'aide d'un envoi non bloquant. Les adaptateurs qui utilisent des envois bloquants n’avez pas besoin d’appeler cette méthode, car le moteur de messagerie va entraîner sa suppression sur le nom de l’adaptateur si l’adaptateur retourne `true` de **TransmitMesssage**.|  
|**MoveToSuspendQ**|MoveToSuspendQ|Place un message dans la file d'attente de messages interrompus.|  
|**Soumettez à nouveau**|Resubmit|Demande qu'un message fasse l'objet d'un nouvel essai de transmission plus tard. Cette méthode est généralement appelée après qu'une tentative de transmission a échoué.|  
|**MoveToNextTransport**|MoveToNextTransport|Demande qu'un message soit transmis à l'aide de son transport secondaire. Cette méthode est généralement appelée lorsque le nombre maximal de tentatives est atteint. En l'absence de transport secondaire, cette méthode échoue.|  
|**SubmitRequestMessage**|SubmitRequest|Envoie un message de requête. Il s'agit d'un message de requête d'une paire requête-réponse.|  
|**CancelRequestForResponse**|CancelRequestForResponse|Notifie le moteur que l'adaptateur ne souhaite plus attendre le message de réponse d'une paire requête-réponse.|  
|**Désactiver**|N/A|Supprime toutes les tâches du lot.|  
|**Terminé**|N/A|Envoie un lot de messages à traiter au moteur.|  
  
## <a name="batch-management"></a>Gestion des lots  
 Les lots sont implémentés en code natif au sein du moteur de messagerie. C'est pourquoi un adaptateur écrit en code géré devrait libérer le wrapper RCW (Runtime Callable Wrapper) pour le lot après avoir terminé le traitement du lot. Cette opération est effectuée en code géré à l’aide de la **Marshal.ReleaseComObject** API. Il est important de souligner que cette API doit être appelée dans une boucle while tant que le nombre de références renvoyé atteigne zéro.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] traite de façon synchrone les messages d'un lot. De nombreux lots pouvant être traités en même temps, ceci peut être une occasion pour optimiser l'adaptateur en ajustant la taille de lot dans le domaine d'application. Supposons, par exemple, que vous voulez traiter tous les fichiers d'un FTP (jusqu'à ce qu'une limite donnée soit atteinte) ou dans le cas de SAP, vous voulez traiter un seul flux dans un nombre de messages envoyés en tant que lot.  
  
 Le lot utilisé par un adaptateur pour repasser les opérations à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas nécessairement besoin de correspondre exactement à la liste de messages que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] donne à l'adaptateur. En d’autres termes, lorsque envois transactionnels, vous devez fractionner les opérations de renvoi **MoveToNextTransport** et **MoveToSuspendQ** dans des lots distincts. De nombreux adaptateurs trient les lots de messages envoyés destinés à plusieurs points de terminaison dans des listes de messages distinctes qui feront l'objet de davantage de traitement.  
  
 En résumé, dans[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], il n'existe aucune règle (outre celles associées à la transaction) associée au traitement par lot des messages. Le traitement par lot est simplement un moyen spécifique à l'implémentation dont dispose l'adaptateur pour découper les messages allant vers [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou sortant de celui-ci.  
  
 Un adaptateur peut créer des lots de messages en regroupant des lots plus petits que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] a fourni en lot volumineux en réponse à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez optimiser de manière sensible les adaptateurs transactionnels amenés à traiter de grands nombres de très petits messages. Cela réduit le rapport nombre de transactions par message.  
  
 En règle générale, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] produit côté envoi des lots comportant entre 5 et 10 messages. S'il s'agit de très petits messages, un adaptateur peut regrouper jusqu'à 100 messages dans un lot avant de renvoyer un lot transactionnel de suppressions à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Une telle optimisation n'est pas facile à implémenter. Vous devez vous assurer que les messages ne restent jamais coincés dans la mémoire de l'adaptateur en attendant indéfiniment qu'un seuil quelconque soit atteint.  
  
 L'importance du traitement par lot est visible au niveau des statistiques de performances de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] concernant les adaptateurs à débit élevé, tels que MQSeries. Dans le cas de ces adaptateurs, les messages sont reçus au moins deux fois plus souvent qu'ils ne sont envoyés. Par défaut, l'adaptateur de réception utilise des lots de 100 messages alors que l'adaptateur d'envoi utilise les lots [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] par défaut qui lui sont donnés.  
  
## <a name="transactional-batches"></a>Lots transactionnels  
 Lorsque vous écrivez le code d'un adaptateur qui crée un objet transactionnel et le remet à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous prenez la responsabilité que le code :  
  
-   Décide du résultat final de l’opération de traitement par lots : pour valider ou pour terminer la transaction. Cette décision peut dépendre d'autres branches transactionnelles au sein de l'étendue de cette transaction qui ne dépendent pas de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Il peut s'agir notamment de l'écriture dans une file d'attente Message Queuing (MSMQ) ou d'une opération de base de données transactionnelle ;  
  
-   Informe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] du résultat final en appelant le **IBTDTCCommitConfirm.DTCCommitConfirm** (méthode). Renvoie `true` pour indiquer la réussite de la validation de la transaction et `false` pour indiquer l'échec et l'annulation de la transaction.  
  
 L'adaptateur doit informer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] du résultat final de la transaction pour pouvoir tenir à jour ses données de suivi internes. L’adaptateur informe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] du résultat final en appelant **DTCCommitConfirm**. S'il ne le fait pas, une fuite de mémoire sensible se produit et la transaction MSDTC expire, puis échoue bien que ses opérations aient réussi.