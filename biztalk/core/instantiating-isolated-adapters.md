---
title: "Instanciation d’adaptateurs isolés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b8359a3-b098-4bb6-87b4-d3432d2671b1
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e3090252f63221547604a4fdf88388bcbf8296f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="instantiating-isolated-adapters"></a><span data-ttu-id="ef0c7-102">Instanciation d'adaptateurs isolés</span><span class="sxs-lookup"><span data-stu-id="ef0c7-102">Instantiating Isolated Adapters</span></span>
<span data-ttu-id="ef0c7-103">Comme indiqué précédemment, les adaptateurs ne sont pas instanciés par BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="ef0c7-103">As discussed earlier, isolated adapters are not instantiated by BizTalk Server.</span></span> <span data-ttu-id="ef0c7-104">Au lieu de cela, ils sont instanciés et hébergés dans un autre processus.</span><span class="sxs-lookup"><span data-stu-id="ef0c7-104">Rather, they are instantiated and hosted in another process.</span></span> <span data-ttu-id="ef0c7-105">Il incombe à l’adaptateur pour créer son proxy de transport, **QueryInterface**, pour **IBTTransportProxy**, puis appelez **IBTTransportProxy**. **RegisterIsolatedReceiver** à inscrire avec le moteur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="ef0c7-105">It is the responsibility of the adapter to create its transport proxy, **QueryInterface**, for **IBTTransportProxy**, and then call **IBTTransportProxy**.**RegisterIsolatedReceiver** to register with the Messaging Engine.</span></span>  
  
 <span data-ttu-id="ef0c7-106">Cette inscription implique que l'adaptateur envoie l'un de ses emplacements de réception configurés et activés au moteur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="ef0c7-106">Registration requires that the adapter pass one of its configured and enabled receive locations to the Messaging Engine.</span></span> <span data-ttu-id="ef0c7-107">Les informations d'identification du processus hôte de l'adaptateur doivent être membres du groupe Utilisateurs d'hôtes BizTalk isolés.</span><span class="sxs-lookup"><span data-stu-id="ef0c7-107">The adapter's host process credentials must be a member of the BizTalk Isolated Host Users group.</span></span> <span data-ttu-id="ef0c7-108">La simple utilisation de l'emprunt d'identité est dans ce cas insuffisante, sauf si l'utilisateur est membre de ce groupe.</span><span class="sxs-lookup"><span data-stu-id="ef0c7-108">Simply using impersonation here is insufficient unless the user is a member of that group.</span></span> <span data-ttu-id="ef0c7-109">En outre, l’adaptateur est interrogé pour vous assurer qu’il possède la bonne **ClassID** et est en cours d’exécution sur l’ordinateur qui a été configurée pour cette instance d’hôte.</span><span class="sxs-lookup"><span data-stu-id="ef0c7-109">In addition, the adapter is queried to ensure it has the correct **ClassID** and is running on the computer that was configured for that host instance.</span></span> <span data-ttu-id="ef0c7-110">Une fois que l’adaptateur est inscrit auprès de son proxy de transport, sa configuration est envoyée à l’aide en appelant la méthode Load de la **IPersistPropertyBag** interface.</span><span class="sxs-lookup"><span data-stu-id="ef0c7-110">After the adapter has successfully registered with its transport proxy, its configuration is sent to it using by calling the Load method of the **IPersistPropertyBag** interface.</span></span>  
  
 <span data-ttu-id="ef0c7-111">Le schéma ci-dessous illustre cette séquence d'appels d'API :</span><span class="sxs-lookup"><span data-stu-id="ef0c7-111">The following figure illustrates this sequence of API calls.</span></span> <span data-ttu-id="ef0c7-112">l'adaptateur implémente les interfaces encadrées en bleu.</span><span class="sxs-lookup"><span data-stu-id="ef0c7-112">The interfaces in blue are implemented by the adapter.</span></span>  
  
 ![](../core/media/isolated-adapter-init.gif "Isolated_adapter_init")  
  
 <span data-ttu-id="ef0c7-113">L'extrait de code suivant illustre les appels d'API d'inscription :</span><span class="sxs-lookup"><span data-stu-id="ef0c7-113">The following code fragment illustrates the registration API calls:</span></span>  
  
```  
using Microsoft.BizTalk.TransportProxy.Interop;  
using Microsoft.BizTalk.Component.Interop;  
using Microsoft.BizTalk.Message.Interop;  
  
public class MyAdapter : IBTTransport,   
 IBTTransportConfig,   
 IBTTransportControl,   
 IBaseComponent  
{  
...  
private IBTTransportProxy transportProxy;  
  
 public void Register(string uri)  
 {  
 // Create the Transport Proxy...  
 this.transportProxy =   
 (IBTTransportProxy)new BTTransportProxy();  
  
// Register on of the adapters uri’s with the TP  
 this.transportProxy.RegisterIsolatedReceiver(  
 uri,   
 (IBTTransportConfig)this );  
 }  
}  
```  
  
 <span data-ttu-id="ef0c7-114">**Conseil pour l’implémentation :** nous recommandons que l’adaptateur conserve un décompte du travail en cours.</span><span class="sxs-lookup"><span data-stu-id="ef0c7-114">**Implementation Tip:** We recommend that the adapter keep a count of the work in progress.</span></span> <span data-ttu-id="ef0c7-115">L’adaptateur doit bloquer **Terminate** jusqu'à ce que le nombre de messages a atteint zéro.</span><span class="sxs-lookup"><span data-stu-id="ef0c7-115">The adapter should block **Terminate** until the message count has reached zero.</span></span> <span data-ttu-id="ef0c7-116">Au niveau de la réception, cela inclut les demandes en suspens qui n'ont pas été publiées dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="ef0c7-116">On the receive side this work includes any outstanding requests that have not been published to BizTalk Server.</span></span> <span data-ttu-id="ef0c7-117">Messages de réponse ne sont pas remis à un adaptateur de réception après **Terminate** a été appelée.</span><span class="sxs-lookup"><span data-stu-id="ef0c7-117">Response messages are not delivered to a receive adapter after **Terminate** has been called.</span></span>  
  
 <span data-ttu-id="ef0c7-118">Pour les adaptateurs d'envoi, les messages en cours de traitement doivent être traités de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="ef0c7-118">For send adapters, messages that are in progress should be handled appropriately.</span></span> <span data-ttu-id="ef0c7-119">Cela signifie que les messages correctement remis doivent être supprimés de la file d'attente de messages de l'application privée de l'adaptateur afin d'éviter qu'ils ne soient envoyés plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="ef0c7-119">This means any message that was successfully delivered should be deleted from the adapter's private application message queue to prevent messages from being sent more than once.</span></span>  
  
 <span data-ttu-id="ef0c7-120">Après avoir **Terminate** est appelé le moteur de messagerie n’accepte pas les demandes de publication des nouveaux messages, à l’exception des messages de réponse des paires sollicitation-réponse.</span><span class="sxs-lookup"><span data-stu-id="ef0c7-120">After **Terminate** is called the Messaging Engine does not accept requests to publish new messages, with the exception of response messages for solicit-response pairs.</span></span>