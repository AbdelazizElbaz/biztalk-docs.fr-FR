---
title: "FAQ sur les adaptateurs WCF : Utilisation des Services WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: befa2268-8a65-465f-8086-70a66808845e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41d02fe0b7be1f53edaac4c18cfd7717a25c3a71
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="wcf-adapter-faq-using-wcf-services"></a>FAQ sur les adaptateurs WCF : utilisation des services WCF
## <a name="how-does-biztalk-server-use-its-wcf-adapters-to-access-wcf-services"></a>Comment BizTalk Server utilise-t-il les adaptateurs WCF pour accéder aux services WCF ?  
 Les adaptateurs WCF BizTalk sont configurés dans BizTalk Server via un emplacement de réception ou un port d'envoi WCF. Lorsqu'un emplacement de réception utilisant un adaptateur WCF est activé, une instance ServiceHost unique est instanciée et initialisée pour chaque emplacement de réception. L'instance ServiceHost exécute un service générique qui accepte des messages WCF entrants, puis les convertit en messages BizTalk avant de les publier dans la base de données MessageBox BizTalk. Le service ServiceHost générique est interne à l'implémentation de l'adaptateur de réception WCF BizTalk et expose un contrat sans type. Dans WCF, un contrat sans type se compose de signatures d'opération qui prennent un paramètre de type WCF System.ServiceModel.Channel.Message.  
  
 L'opération d'un service WCF doit être marquée comme IsOneWay=false si elle doit être accessible par un port d'envoi BizTalk même s'il n'y aucune donnée à renvoyer. Les opérations sur le contrat côté client doivent être annotées IsOneWay=false et ReplyAction=”*”.  En outre, tous les appels provenant du client doivent être marqués comme IsOneWay=”false”. Une opération de service bidirectionnelle peut renvoyer une valeur de type Message. Une exception à cela consiste à utiliser l'adaptateur WCF-NetMsmq puisqu'il exécute une opération unidirectionnelle qui publie un message dans une file d'attente MSMQ. Dans ce cas, le port d'envoi peut être unidirectionnel et chaque opération de service est marquée comme IsOneWay=true.  
  
 Dans WCF, il est également possible de définir un élément OperationContract isOneWay=false sur une méthode renvoyant void. Dans une telle situation, un message est renvoyé sur le câble créé pour vous au moment de l'exécution de WCF.  
  
 Les adaptateurs WCF BizTalk utilisent cette fonctionnalité. Lorsque vous spécifiez un port BizTalk unidirectionnel, vous obtenez une méthode void avec isOneWay=false dans l'implémentation de l'adaptateur WCF. Notez qu'un port unidirectionnel BizTalk utilisant un canal direct comme HTTP ou net.tcp correspond en fait à un élément OperationContract isOneWay=false. Les canaux mis en file d'attente comme net.msmq sont différents, car il arrive qu'un port BizTalk unidirectionnel communique avec un OperationContract isOneWay=true. La situation est différente, car le distributeur WCF utilise une transaction sur le canal.  
  
## <a name="how-do-you-create-and-use-a-custom-binding-with-a-wcf-custom-adapter"></a>Création et utilisation d'une liaison personnalisée avec un adaptateur WCF personnalisé  
 Une liaison CustomBinding WCF est composée d'un regroupement d'éléments BindingElements. Elle peut être créée soit en extrayant divers éléments BindingElements préexistants (par exemple, en combinant un transport préexistant avec l'encodeur préexistant d'une autre source), soit en combinant un élément BindingElement préexistant avec un élément BindingElement personnalisé récemment écrit. Un élément CustomBinding peut être généré dans le code à partir de ces composants BindingElements en les ajoutant par programme. WCF permet également cette construction via la configuration .NET (fichiers de configuration). À l'aide de BizTalk Server, cet élément CustomBinding peut être créé via l'adaptateur WCF BizTalk personnalisé.  
  
 L'adaptateur WCF BizTalk personnalisé permet de déployer une nouvelle liaison à partir des éléments BindingElements, ainsi que de configurer directement une nouvelle liaison. Il permet également de configurer les comportements sur les liaisons standard. Ceci est particulièrement utile car l'écriture de comportements personnalisés est bien plus facile que l'écriture de nouveaux objets BindingElements.  
  
 Création d’un élément BindingElement est un exercice de développement impliquées et la meilleure source d’informations de référence pour qu’il est exemples WCF sur le lien hypertexte « http://go.microsoft.com/fwlink/?LinkId=142449 » \t « _blank » http://go.microsoft.com/fwlink/?LinkId=142449. Pour créer un élément BindingElement personnalisé, vous créez une classe dérivant de BindingElement. Un nouvel élément BindingElement doit se trouver dans un nouvel assembly. Celui-ci doit être installé dans le GAC de l'ordinateur d'administration dans lequel sont configurés l'hôte, le port d'envoi et l'emplacement de réception BizTalk. Pour associer une liaison personnalisée avec un port d’envoi ou emplacement de réception, vous devez d’abord ajouter à la \<bindingElementExtensions\> section du fichier machine.config sur le même ordinateur.  
  
 Après avoir apporté cette modification, vous pouvez afficher le **Configuration des propriétés de Transport** boîte de dialogue pour configurer la liaison.  
  
1.  Sur le **liaison** onglet, le type de liaison, sélectionnez **customBinding**.  
  
2.  Dans le **liaison** volet, avec le bouton droit **CustomBindingElement**, puis sélectionnez **Ajout d’une Extension**.  
  
3.  Sélectionnez l'élément de liaison que vous avez spécifié dans le fichier machine.config, puis configurez la liaison selon vos besoins. La liaison peut à présent utiliser la transmission ou la réception de messages.  
  
 BizTalk utilise une validation très limitée pour une liaison personnalisée lorsque celle-ci a été ajoutée de cette manière. Toutefois, il est important de vérifier que les éléments de liaison sont répertoriés dans le bon ordre. L'élément de liaison qui doit être invoqué en premier au moment de l'exécution doit être en bas de l'arborescence des liaisons CustomBindingElement dans la boîte de dialogue. La liste des éléments BindingElements doit contenir un transport, qui doit être en bas de la liste. L'ensemble d'éléments BindingElements doit également contenir un encodeur. Pour plus d’informations, consultez la documentation WCF sur la liaison d’éléments à [http://go.microsoft.com/fwlink/?LinkId=142449](http://go.microsoft.com/fwlink/?LinkId=142449).  
  
## <a name="what-is-a-wcf-custom-behavior-and-how-do-i-use-one-with-biztalk-server"></a>Définition d'un comportement WCF personnalisé et utilisation de celui-ci avec BizTalk Server  
 L'un des avantages d'utiliser WCF en tant que mécanisme de communication par message est la possibilité d'étendre les fonctionnalités de ses services à l'aide d'un code personnalisé. Les extensions de comportement personnalisé sont l'une des fonctionnalités qui différencie WCF des autres technologies de services Web sur le marché.  
  
 Différents points du flux d'un message WCF interceptent et exécutent un traitement personnalisé avant que le message n'atteigne sa destination finale. Les extensions de comportement personnalisé WCF sont l'un de ces mécanismes d'interception. Elles peuvent permettre d'étendre le service WCF ou la fonctionnalité client à différents niveaux de granularité. Elles peuvent exister aux niveaux du service et du client WCF. La configuration d'un comportement sur la pile d'appels vers un service WCF n'a aucune incidence sur la liaison de communication utilisée pour l'appel. En fait, les comportements sont généralement invisibles au client car ils ne sont pas affichés dans les métadonnées qu'un service publie. Le client ne se rend habituellement pas compte que des comportements sont exécutés lors d'un appel vers une opération WCF.  
  
 La capacité à implémenter facilement un traitement personnalisé dans un appel vers un service WCF est l'une des raisons pour lesquelles WCF est un paradigme de programmation riche, en comparaison avec d'autres méthodes de communication entre les applications Web. Le traitement personnalisé peut prendre la plupart des formes, selon les besoins d'extensibilité de l'application Web. Les développeurs peuvent créer des extensions personnalisées qui inspectent et valident la configuration du service, ou modifient le comportement à l'exécution dans les applications de client et de service WCF. Comportements peuvent compléter le traitement normal des messages, modifiez le message au cours du traitement, vérifier certains critères de configuration et prenez les mesures appropriées, valider les identités de l’appelant et passer le message si elle est réussie, etc. Car il s’agit réellement personnalisé mécanisme vous implémentez toutes les extensions de traitement votre application a besoin.  
  
 Pour utiliser un comportement personnalisé WCF dans BizTalk Server vous allez le configurer à l’aide de la **comportement** onglet de l’adaptateur WCF-Custom ou WCF-CustomIsolated pour un emplacement de réception ou un port d’envoi.