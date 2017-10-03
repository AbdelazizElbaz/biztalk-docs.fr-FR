---
title: "Architecture de l’adaptateur d’envoi SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e52a5a21-0aa1-4cd9-a2a4-f9df425913a0
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d772203c980495c5aa62266beb060693c1a8ad8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-send-adapter-architecture"></a>Architecture de l’adaptateur envoi SWIFT
En général, les adaptateurs d’envoi de BizTalk Server sont hébergées dans le processus du service BizTalk, Btsntsvc.exe. Cela signifie que BizTalk Server gère la durée de vie de l’adaptateur.  
  
 Il existe deux façons d’envoyer des messages au réseau rapide : (ExchangeRequest) synchrone et asynchrones (non implémenté pour cette version). Dans BizTalk Server, l’adaptateur d’envoi doit prendre en charge les modèles de communication suivants pour interagir avec le moteur de messagerie BizTalk :  
  
-   Sollicitation-réponse, les messages sont échangés par paires, appelées les primitives, avec le réseau rapide. Tous les messages envoyés à SWIFT aura une réponse qu’il s’agisse d’entreprise, d’accusé de réception ou d’erreur. Le message de réponse est envoyé vers messagebox. Ce mode de fonctionnement est utilisé pour la communication en temps réel.  
  
-   Envoi unidirectionnel, l’adaptateur configuré dans une façon fonctionne dans le magasin et le mode de transfert. Les messages sont envoyés à une file d’attente préconfiguré par opposition à un destinataire. L’expéditeur peut récupérer la réponse en ouvrant une session avec la file d’attente en mode push ou pull.  
  
> [!NOTE]
>  La procédure de création de l’adaptateur affecte la façon dont il fonctionne.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Adaptateur d’envoi SWIFT URI](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-uri.md)  
  
-   [Envoi dynamique de l’adaptateur envoi SWIFT](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-dynamic-send.md)  
  
-   [Initialisation de l’adaptateur envoi SWIFT](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-initialization.md)  
  
-   [Mode synchrone de l’adaptateur envoi SWIFT](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-synchronous-mode.md)  
  
-   [Arrêt de l’adaptateur envoi SWIFT](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-termination.md)