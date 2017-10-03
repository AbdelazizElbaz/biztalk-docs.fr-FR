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
# <a name="instantiating-isolated-adapters"></a>Instanciation d'adaptateurs isolés
Comme indiqué précédemment, les adaptateurs ne sont pas instanciés par BizTalk Server. Au lieu de cela, ils sont instanciés et hébergés dans un autre processus. Il incombe à l’adaptateur pour créer son proxy de transport, **QueryInterface**, pour **IBTTransportProxy**, puis appelez **IBTTransportProxy**. **RegisterIsolatedReceiver** à inscrire avec le moteur de messagerie.  
  
 Cette inscription implique que l'adaptateur envoie l'un de ses emplacements de réception configurés et activés au moteur de messagerie. Les informations d'identification du processus hôte de l'adaptateur doivent être membres du groupe Utilisateurs d'hôtes BizTalk isolés. La simple utilisation de l'emprunt d'identité est dans ce cas insuffisante, sauf si l'utilisateur est membre de ce groupe. En outre, l’adaptateur est interrogé pour vous assurer qu’il possède la bonne **ClassID** et est en cours d’exécution sur l’ordinateur qui a été configurée pour cette instance d’hôte. Une fois que l’adaptateur est inscrit auprès de son proxy de transport, sa configuration est envoyée à l’aide en appelant la méthode Load de la **IPersistPropertyBag** interface.  
  
 Le schéma ci-dessous illustre cette séquence d'appels d'API : l'adaptateur implémente les interfaces encadrées en bleu.  
  
 ![](../core/media/isolated-adapter-init.gif "Isolated_adapter_init")  
  
 L'extrait de code suivant illustre les appels d'API d'inscription :  
  
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
  
 **Conseil pour l’implémentation :** nous recommandons que l’adaptateur conserve un décompte du travail en cours. L’adaptateur doit bloquer **Terminate** jusqu'à ce que le nombre de messages a atteint zéro. Au niveau de la réception, cela inclut les demandes en suspens qui n'ont pas été publiées dans BizTalk Server. Messages de réponse ne sont pas remis à un adaptateur de réception après **Terminate** a été appelée.  
  
 Pour les adaptateurs d'envoi, les messages en cours de traitement doivent être traités de manière appropriée. Cela signifie que les messages correctement remis doivent être supprimés de la file d'attente de messages de l'application privée de l'adaptateur afin d'éviter qu'ils ne soient envoyés plusieurs fois.  
  
 Après avoir **Terminate** est appelé le moteur de messagerie n’accepte pas les demandes de publication des nouveaux messages, à l’exception des messages de réponse des paires sollicitation-réponse.