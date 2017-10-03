---
title: "Modèles d’échange pour les adaptateurs d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ad65fb5-640d-4bd2-aabe-946210f58a22
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 997aaa9a92f90f30bdaaeb59cc9cecb0c454496f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exchange-patterns-for-send-adapters"></a>Remplacement des modèles pour les adaptateurs d'envoi
Les adaptateurs d'envoi sont des messages remis du moteur de messagerie BizTalk à transmettre sur le câble. Ces messages peuvent être envoyés via un modèle d'échange de message unidirectionnel ou bidirectionnel. Un adaptateur qui traite ce modèle d'échange de message bidirectionnel est nommé adaptateur de sollicitation-réponse.  
  
## <a name="blocking-vs-non-blocking-transmissions"></a>Blocage de Visual Studio. Transmissions non bloquantes  
 Le moteur de messagerie remet les messages à l’adaptateur d’envoi à l’aide du **IBTTransmitter.TransmitMessage** méthode ou la **IBTTransmitterBatch.TransmitMessage** (méthode), selon que l’adaptateur prend en charge de traitement par lots. Les deux versions de la méthode comportent une valeur de retour booléenne qui indique comment l'adaptateur a transmis le message. Si l'adaptateur retourne `true`, il a complètement envoyé le message avant de renvoyer. Dans ce cas, le moteur de messagerie supprime le message de la base de données MessageBox pour l'adaptateur. Si l'adaptateur renvoie `false`, il a commencé à transmettre le message et a renvoyé avant la fin de la transmission. Dans ce cas, l'adaptateur est responsable non seulement de la suppression du message de la file d'attente de son application mais aussi du traitement des erreurs de transmission qui nécessitent que le message soit extrait pour être transmis ou suspendu.  
  
 L’adaptateur retournant `false` est un appel non bloquant, ce qui signifie que la **TransmitMessage** code d’implémentation ne bloque pas le thread appelant du moteur de messagerie. L'adaptateur ajoute simplement le message à une file d'attente en mémoire prête à être transmise puis renvoie. L'adaptateur doit normalement disposer de sa propre réserve de threads qui traite la file d'attente en mémoire, transmet le message, puis informe le moteur du résultat de la transmission.  
  
 Les threads du moteur de messagerie sont généralement plus liés au processeur que ceux utilisés pour envoyer des données sur le réseau. L'utilisation combinée ces deux types de threads affecte les performances. Les envois non bloquants permettent de découpler ces deux types de threads et améliorent sensiblement les performances par rapport aux appels bloquants.  
  
 Le diagramme suivant présente la réserve de threads de l'adaptateur qui peuvent avoir tendance à être liés par les opérations d'E/S. La réserve de threads du moteur de messagerie BizTalk Server est davantage liée au traitement effectué par le processeur. En conservant deux réserves de threads différentes et en ne combinant pas le même type de thread, le système opère plus efficacement.  
  
 ![](../core/media/io-cpu-bound-threadpools.gif "Io_cpu_bound_threadpools")  
  
 **Conseil de performances :** pour des performances optimales, adaptateurs d’envoi sont non bloquant et reconnaissent les lots. Lorsque l'adaptateur BizTalk File est passé de bloquant et ne reconnaissant pas les lots à non bloquant et reconnaissant les lots, les performances ont été multipliées par trois.  
  
 **Conseil de dépannage :** transmet de blocage peut entraîner une dégradation des performances d’une instance de l’intégralité de l’hôte. Si l’adaptateur effectue un blocage excessif **TransmitMessage** cela empêchera les threads du moteur de remettre des messages à d’autres cartes.  
  
## <a name="non-batched-sends"></a>Envois hors lots  
 Les adaptateurs qui ne sont pas reconnaissent les lots doivent implémenter **IBTTransmitter** comme détaillé dans [Interfaces pour un adaptateur d’envoi asynchrone](../core/interfaces-for-an-asynchronous-send-adapter.md). Pour chaque message que l’adaptateur doit transmettre le moteur de messagerie appelle **IBTTransmitter.TransmitMessage**. Le diagramme d'interaction d'objets ci-dessous décrit la méthode standard de transmission des messages, qui comporte les étapes suivantes :  
  
1.  Le moteur remet le message à l'adaptateur.  
  
2.  L'adaptateur place le message dans une file d'attente en mémoire prête à être transmise.  
  
3.  Un thread de la réserve de threads de l'adaptateur extrait le message de la file d'attente, lit la configuration du message, puis transmet le message sur le réseau.  
  
4.  L'adaptateur reçoit un nouveau lot du moteur.  
  
5.  L’adaptateur appelle la méthode **DeleteMessage** sur le lot, en passant le message qu’il vient de transmettre.  
  
6.  L’adaptateur appelle la méthode **fait** sur le lot.  
  
7.  Le moteur traite le lot et supprime le message de la file d'attente de l'application.  
  
8.  Le moteur rappelle l’adaptateur pour l’informer du résultat de la **DeleteMessage** opération.  
  
 ![](../core/media/deleting-from-message-queue.gif "Deleting_from_message_queue")  
  
 Le diagramme d'interaction d'objets précédent présente l'adaptateur supprimant un seul message de la file d'attente de l'application. L'idéal est que l'adaptateur regroupe les opérations de message plutôt que d'opérer sur un seul message à la fois.  
  
## <a name="batched-sends"></a>Envois par lots  
 Adaptateurs qui reconnaissent les lots doivent implémenter **IBTBatchTransmitter** et **IBTTransmitterBatch** comme détaillé dans [Interfaces pour les adaptateurs d’envoi](../core/interfaces-for-send-adapters.md). Lorsque le moteur dispose de l’adaptateur transmettre les messages, le moteur reçoit un nouveau lot de l’adaptateur en appelant **IBTBatchTransmitter.GetBatch**. L’adaptateur retourne un nouvel objet de lot qui implémente **IBTTransmitterBatch**. Le moteur commence alors le lot en appelant **IBTTransmitterBatch.BeginBatch**. Cette API dispose d'un paramètre Out qui permet à l'adaptateur de spécifier le nombre maximal de messages qu'il accepte dans le lot. Le cas échéant, l'adaptateur peut retourner une transaction DTC. Le moteur appelle **IBTTransmitterBatch.TransmitMessage** une fois pour chaque message sortant à ajouter au lot. Le nombre d'appels est supérieur à zéro mais inférieur ou égal à la taille maximale du lot indiquée par l'adaptateur. Lorsque tous les messages ont été ajoutés au lot, l’adaptateur appelle **IBTTransmitterBatch.Done**. À ce stade, l'adaptateur place généralement tous les messages du lot dans sa file d'attente en mémoire. L'adaptateur transmet les messages d'un ou plusieurs threads de sa propre réserve de threads comme dans le cas des adaptateurs ne reconnaissant pas les lots. Il informe ensuite le moteur du résultat de la transmission.  
  
 Le diagramme d'interaction d'objets suivant présente la transmission de deux messages par un adaptateur d'envois par lots.  
  
 ![](../core/media/batchedsends.gif "BatchedSends")  
  
## <a name="handling-transmission-failures"></a>Gestion des erreurs de transmission  
 La sémantique recommandée pour les erreurs de transmission est présentée dans la figure ci-dessous. Il ne s'agit que de recommandations non appliquées par le moteur de messagerie. Si besoin, vous pouvez développer un adaptateur ne suivant pas ces directives, mais dans ce cas procédez avec précaution. Par exemple, en règle générale, un adaptateur doit toujours déplacer les messages vers le transport secondaire une fois le nombre maximal de tentatives atteint.  
  
 Plus généralement, un transport peut avoir besoin d'utiliser plus de tentatives que le nombre de tentatives défini. Bien qu'il s'agisse d'un cas légèrement différent, ceci est acceptable car la couche de transport s'en trouve alors plus tolérante. En général, les API exposées par le moteur de messagerie sont conçues pour permettre à l'adaptateur un contrôle maximal lorsque cela est possible. Ce contrôle s'accompagne d'un niveau de responsabilité plus élevé.  
  
 ![](../core/media/handlingerrors.gif "HandlingErrors")  
  
 L’adaptateur détermine le nombre de nouvelles tentatives disponibles sur un message en activant la propriété de contexte système **RetryCount**. L’adaptateur appelle la **renvoyer** API qu’une seule fois pour chaque nouvelle tentative tentative et transmet le message à renvoyer. Il transmet également l'horodatage indiquant quand le moteur doit remettre à nouveau le message à l'adaptateur. Cette valeur doit être généralement l’heure actuelle plus la valeur de **RetryInterval**. **RetryInterval** est une propriété de contexte système dont les unités sont les minutes. Les deux le **RetryCount** et **RetryInterval** dans le contexte du message sont les valeurs qui sont configurés sur le port d’envoi. Considérez un déploiement évolutif avec les instances du même hôte BizTalk déployées sur plusieurs ordinateurs. Si le message est remis une fois l'intervalle de nouvelle tentative expiré, il peut être remis à n'importe laquelle des instances de l'hôte sur n'importe quel ordinateur où ces instances sont configurées pour s'exécuter. Pour cette raison, l'adaptateur ne doit conserver aucun état associé à un message à utiliser avec la nouvelle tentative car rien ne garantit que la même instance de l'adaptateur sera responsable de la transmission par la suite.  
  
 L'adaptateur doit uniquement tenter de déplacer le message vers le transport secondaire une fois le nombre de tentatives inférieur ou égal à zéro. Une tentative de déplacement du message vers le transport secondaire échoue si aucun transport secondaire n'est configuré pour le port. Dans ce cas, le message doit être suspendu.  
  
 Le fragment de code suivant indique comment déterminer le nombre de tentatives et l'intervalle à partir du contexte du message, ainsi que le nouvel envoi ou le déplacement suivant vers le transport secondaire.  
  
```  
using Microsoft.XLANGs.BaseTypes;  
using Microsoft.BizTalk.Message.Interop;  
using Microsoft.BizTalk.TransportProxy.Interop;  
 …  
// RetryCount and RetyInterval are system context properties...  
private static readonly PropertyBase RetryCountProperty =   
 new BTS.RetryCount();  
private static readonly PropertyBase RetryIntervalProperty =   
 new BTS.RetryInterval();  
  
public void HandleRetry(IBaseMessage msg, IBTTransportBatch batch)  
{  
int retryCount = 0;  
int retryInterval = 0;  
  
// Get the RetryCount and RetryInterval off the msg ctx...  
 GetMessageRetryState(msg, out retryCount, out retryInterval);  
  
// If we have retries available resubmit, else move to   
 // backup transport...  
 if ( retryCount > 0 )  
batch.Resubmit(  
 msg, DateTime.Now.AddMinutes(retryInterval));  
else  
batch.MoveToNextTransport(msg);  
}  
  
public void GetMessageRetryState(  
 IBaseMessage msg,   
 out int retryCount,   
 out int retryInterval )  
{  
retryCount = 0;  
retryInterval = 0;  
  
object obj =  msg.Context.Read(  
RetryCountProperty.Name.Name,    
RetryCountProperty.Name.Namespace);   
  
if ( null != obj )  
retryCount = (int)obj;  
  
obj =  msg.Context.Read(  
RetryIntervalProperty.Name.Name,    
RetryIntervalProperty.Name.Namespace);   
  
if ( null != obj )  
retryInterval = (int)obj;  
}  
```  
  
## <a name="throwing-an-exception-from-transmitmessage"></a>Génération d'une exception à partir de TransmitMessage  
 Si l’adaptateur lève une exception sur chacune des API **IBTTransmitter.TransmitMessage**, **IBTTransmitterBatch.TransmitMessage**, **IBTTransmitterBatch.Done**, moteur traite la transmission des messages impliqués en tant qu’erreurs de transmission et prend les mesures appropriées pour le message, comme détaillé dans [comment gérer les défaillances d’adaptateur](../core/how-to-handle-adapter-failures.md).  
  
 Pour les adaptateurs d'envoi reconnaissant les lots, la génération d'une exception sur l'API TransmitMessage a pour résultat d'effacer le lot entier et d'effectuer les opérations d'échec de transmission par défaut pour tous les messages de ce lot.  
  
## <a name="solicit-response"></a>Sollicitation-réponse  
 Les adaptateurs d'envoi bidirectionnels prennent généralement en charge les transmissions unidirectionnelles et bidirectionnelles. L’adaptateur d’envoi détermine si le message doit être transmis en tant qu’un envoi unidirectionnel ou bidirectionnel en examinant le **IsSolicitResponse** propriété de contexte système dans le contexte du message.  
  
 Le fragment de code suivant illustre ceci :  
  
```  
private bool portIsTwoWay = false;  
private static readonly PropertyBase IsSolicitResponseProperty= new BTS.IsSolicitResponse();  
  
...  
  
 // Port is one way or two way...  
 object obj =  this.message.Context.Read(  
 IsSolicitResponseProperty.Name.Name,    
 IsSolicitResponseProperty.Name.Namespace);   
  
if ( null != obj )  
 this.portIsTwoWay = (bool)obj;  
```  
  
 Pendant une transmission de type sollicitation-réponse, l'adaptateur transmet le message de sollicitation. Une fois cette opération effectuée, il envoie la réponse associée et indique au moteur de messagerie de supprimer le message de sollicitation d'origine de la base de données MessageBox. La suppression du message de la file d'attente de l'application doit être effectuée dans le même lot de proxy de transport que l'envoi du message de réponse. Ceci assure l'atomicité de la suppression et de l'envoi de la réponse. Pour que l'atomicité soit totale, l'adaptateur doit utiliser une transaction DTC par laquelle la transmission du message de sollicitation vers une ressource reconnaissant les transactions, l'envoi du message de réponse et la suppression du message de sollicitation figurent toutes dans le contexte de la même transaction DTC. Comme toujours, nous recommandons que le message de sollicitation soit transmis via un envoi non bloquant.  
  
 Le fragment de code suivant illustre les aspects principaux d'un envoi bidirectionnel. Lorsque le moteur appelle **IBTTransmitter.TransmitMessage** l’adaptateur place le message à transmettre à une file d’attente en mémoire. L'adaptateur retourne `false` pour indiquer qu'il effectue un envoi non bloquant. Pool de threads de l’adaptateur (**WorkerThreadThunk**) traite la file d’attente en mémoire et enlève un message à transmettre à une méthode d’assistance. Cette méthode est responsable de l'envoi du message de sollicitation et de la réception du message de réponse. (L'implémentation de cette méthode d'assistance dépasse le cadre de cette rubrique.) Le message de réponse est envoyé au moteur et le message de sollicitation supprimé de la file d'attente de l'application.  
  
```  
using System.Collections;  
using Microsoft.XLANGs.BaseTypes;  
using Microsoft.BizTalk.Message.Interop;  
using Microsoft.BizTalk.TransportProxy.Interop;  
  
     static private Queue _transmitQueue = new Queue();  
  static private IBTTransportProxy _transportProxy = null;   
// IBTTransmitter...  
 public bool TransmitMessage(IBaseMessage msg)  
{  
// Add message to the transmit queue...  
lock(_transmitQueue.SyncRoot)  
 {  
_transmitQueue.Enqueue(msg);  
 }  
  
 return false;  
}  
  
 // Threadpool worker thread...   
private void WorkerThreadThunk()  
{  
try  
{  
 IBaseMessage solicitMsg = null;  
  
 lock(_transmitQueue.SyncRoot)  
 {  
 solicitMsg =   
 (IBaseMessage)_transmitQueue.Dequeue();  
}  
  
 IBaseMessage responseMsg = SendSolicitResponse(   
 solicitMsg );  
Callback cb = new Callback();  
  
IBTTransportBatch batch = _transportProxy.GetBatch(  
 cb, null);  
batch.SubmitResponseMessage( solicitMsg, responseMsg );  
batch.DeleteMessage( solicitMsg );  
batch.Done(null);  
}  
catch(Exception)  
{  
// Handle failure....  
}  
}  
  
static private IBaseMessage SendSolicitResponse(  
 IBaseMessage solicitMsg )  
{  
// Helper method to send solicit message and receive   
 // response message...  
IBaseMessage responseMsg = null;  
return responseMsg;  
}  
```  
  
## <a name="dynamic-sends"></a>Envois dynamiques  
 Les ports d'envoi dynamique ne sont pas associés à une configuration d'adaptateur. Ils utilisent à la place la configuration du gestionnaire pour les propriétés par défaut nécessaires à l'adaptateur pour transmettre les messages sur un port dynamique. Par exemple, un adaptateur HTTP peut avoir besoin d'utiliser un proxy et de fournir des informations d'identification. Le nom d'utilisateur, le mot de passe et le port peuvent être spécifiés dans la configuration du gestionnaire, que l'adaptateur met en cache lors de l'exécution.  
  
 Le moteur de déterminer le protocole de transport un message dynamique à être envoyés sur, la **OutboundTransportLocation** est préfixé avec un alias de l’adaptateur. Un adaptateur peut inscrire un ou plusieurs alias avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] lors de l'installation. Le moteur analyse la **OutboundTransportLocation** au moment de l’exécution pour rechercher une correspondance. L’adaptateur est responsable du traitement du **OutboundTransportLocation** avec ou sans l’alias à ce dernier. La table suivante affiche quelques exemples d'alias inscrits pour des adaptateurs BizTalk prêts à l'emploi.  
  
|Alias d'adaptateur|Adaptateur|Exemple de OutboundTransportLocation|  
|-------------------|-------------|---------------------------------------|  
|HTTP://|HTTP|http://www. MaSociété.com/bar|  
|HTTPS://|HTTP|https://www. MaSociété.com/bar|  
|mailto:|SMTP|mailto:A.User@MyCompany.com|  
|FILE://|FILE|FILE://C:\ MyCompany \\%MessageID%.xml|