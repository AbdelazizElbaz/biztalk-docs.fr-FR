---
title: "Interfaces pour un lot pris en charge par l’adaptateur de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa6ee780-189c-41e3-9ab0-6b869e791c0a
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2de4d27ec65620adbb5428491c5ab1a53300fd7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-a-batch-supported-receive-adapter"></a>Interfaces pour un adaptateur de réception pris en charge par lot
Un adaptateur de réception envoie toujours les messages par lots. Un lot est une unité d'opérations de base de données que vous pouvez utilisez pour les actions autres que l'envoi. Par exemple, un adaptateur de réception peut envoyer un ensemble de messages, en suspendre un autre et en supprimer un troisième dans le même lot. Le regroupement de ces opérations distinctes au sein d'un même lot est vivement recommandé car il permet d'optimiser les performances en minimisant le nombre d'allers-retours obligatoires vers une base de données.  
  
 Les adaptateurs de réception in-process et isolés doivent implémenter les interfaces suivantes pour envoyer des lots de messages au serveur :  
  
-   **IBTTransport**  
  
-   **IBTTransportControl** (adaptateurs in-process uniquement)  
  
-   **IBTTransportConfig**  
  
-   **IBaseComponent**  
  
-   **IPersistPropertyBag**  
  
-   **IBTBatchCallBack**  
  
 Les étapes suivantes décrivent la séquence d'actions effectuée par un adaptateur de réception afin d'envoyer les messages au serveur.  
  
1.  Un adaptateur de réception Obtient le lot du proxy de transport en appelant le **GetBatch** méthode de la **IBTTransportProxy** interface. Dans son appel à **GetBatch** l’adaptateur transmet un pointeur vers son **IBTBatchCallback** implémentation de l’interface.  
  
2.  Un adaptateur ajoute les messages un à la fois dans le lot en appelant le **SubmitMessage** méthode de la **IBTTransportBatch** interface. S’il s’agit d’une opération bidirectionnelle, telles que la messagerie avec sollicitation-réponse, le **SubmitResponseMessage** méthode de cette même interface est appelée pour envoyer le message de réponse.  
  
3.  Lorsque tous les messages ont été ajoutés au lot, l’adaptateur appelle la **fait** méthode de la **IBTTransportBatch** interface soumettre le lot au proxy de transport. Étant donné que recevoir des adaptateurs sont asynchrones par nature, l’adaptateur peut immédiatement obtenir un nouveau lot et commencer à envoyer d’autres messages après avoir appelé **fait**.  
  
4.  Une fois que le lot a été traité, le moteur de messagerie appelle l’adaptateur **BatchComplete** méthode de rappel à l’aide du proxy de transport pour effectuer l’appel réel. Un tableau de **BTBatchOperationStatus** objets contenant l’état de l’envoi est transmis à l’adaptateur. Chaque objet correspond à un type d'opération et contient l'état général de l'opération ainsi que l'état de chaque message pour lequel l'opération a été effectuée. La séquence suivante décrit les actions qu'un adaptateur doit effectuer pour analyser l'état d'un traitement par lot.  
  
    1.  Vérification de l’état général du lot valeur HRESULT est passé en tant que paramètre à la **BatchComplete** (méthode). En cas d'échec, cela signifie qu'au moins une des opérations du lot a échoué. Par conséquent, l'envoi du lot en tant qu'entité unique a échoué. L'adaptateur doit alors tenter d'identifier le(s) message(s) responsable(s) et renvoyer en tant que lot uniquement les messages qui ne sont pas à l'origine de l'échec.  
  
         Si l'état général du lot est une réussite, cela signifie que tous les messages transmis au proxy de transport ont été conservés sur le disque. Toutefois, cela ne veut pas dire que le pipeline a traité tous les messages avec succès. Il est possible que les messages ayant échoué dans le pipeline soient suspendus. Pour les messages qui échouent dans le pipeline, l'état général du lot est une réussite car les données ont été écrites sur le disque.  
  
    2.  Vérifiez l'état de chaque type d'opération dans le paramètre `operationStatus`. Si l’état est **S_OK**, l’envoi pour cette opération a réussi et que vous n’avez pas besoin de vérifier l’état de tous les autres. Si l’état est défini sur **BTS_S_EPM_MESSAGE_SUSPENDED** certains messages ont été interrompues. **BTS_S_EPM_SECURITY_CHECK_FAILED** signifie que certains messages d’échec de l’authentification dans une authentification requise port de réception. Si **E_FAIL** est retourné, ou tout paramètre HRESULT avec une valeur qui est inférieur à zéro, l’envoi du message pour cette opération a échoué.  
  
    3.  Vérifiez l'état de chaque message pour le type d'opération. Pour le type d’opération de soumission, l’état de chaque message est défini sur **S_OK** si l’envoi a réussi. **BTS_S_EPM_MESSAGE_SUSPENDED** est retournée si le message a été interrompu. **BTS_S_EPM_SECURITY_CHECK_FAILED** est retournée si le message d’échec de l’authentification sur un port de réception qui requiert une authentification. **E_BTS_NO_SUBSCRIPTION** revient si il y avait pas d’abonnés pour le message publié. Si **E_FAIL** est retourné, ou tout paramètre HRESULT avec une valeur qui est inférieur à zéro, l’envoi du message a échoué.  
  
    4.  En fonction de votre adaptateur, vous voudrez suspendre les messages qui retournent **E_FAIL** ou tout paramètre HRESULT d’échec.  
  
5.  Le **BatchComplete** méthode doit retourner **S_OK** ou **E_FAIL** pour indiquer le résultat de l’exécution. Si le **BatchComplete** méthode retourne **E_FAIL** ou tout paramètre HRESULT négatif, le proxy de transport consigne une erreur.  
  
 L'illustration suivante indique les interactions d'objets impliquées dans la création d'un adaptateur de réception pris en charge par lot.  
  
 ![](../core/media/ebiz-sdk-devadapter1.gif "ebiz_sdk_devadapter1")  
Workflow d'un adaptateur de réception envoyant un lot de messages  
  
## <a name="see-also"></a>Voir aussi  
 [Variables d’adaptateur](../core/adapter-variables.md)   
 [Développement d’un adaptateur de réception](../core/developing-a-receive-adapter.md)   
 [Instanciation et initialisation un adaptateur de réception](../core/instantiating-and-initializing-a-receive-adapter.md)   
 [Adaptateur de réception des interfaces pour In-Process](../core/interfaces-for-an-in-process-receive-adapter.md)   
 [Adaptateur de réception des interfaces pour un hôte isolé](../core/interfaces-for-an-isolated-receive-adapter.md)   
 [Adaptateur de réception des interfaces pour un transactionnel pris en charge par lot](../core/interfaces-for-a-transactional-batch-supported-receive-adapter.md)   
 [Adaptateur de réception des interfaces pour une demande-réponse synchrone](../core/interfaces-for-a-synchronous-request-response-receive-adapter.md)