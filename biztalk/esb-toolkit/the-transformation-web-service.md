---
title: Le Service Web de Transformation | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 788bf4a9-a63b-4fd3-93a2-6e34a1464049
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5abad7a5a7bae3c76fba58ecd92fc3384df5ca25
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-transformation-web-service"></a>Le Service Web de Transformation
Le service Web de la Transformation permet à des applications externes envoyer un document à une application d’ESB et transformé à l’aide d’un mappage de Microsoft BizTalk déployé. Contrairement à l’agent de la transformation, ce service ne pas achemine les messages via la base de données MessageBox de BizTalk.  
  
 Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] contient deux versions de ce service : une version de ASP.NET (ASMX) et une version de Windows Communication Foundation (WCF). Les noms de service sont **ESB. TransformServices** et **ESB. TransformServices.WCF**, respectivement, et les services exposent une méthode unique :  
  
-   **Transformation.** Cette méthode prend comme paramètres une **chaîne** qui contient le message à transformer et un **chaîne** qui contient le nom qualifié complet d’un mappage déployé dans BizTalk. La méthode retourne un **chaîne** qui contient le document transformé. L’utilisation de paramètres de chaîne réduit le risque de problèmes d’interopérabilité dans un environnement hétérogène ; Toutefois, gardez à l’esprit que cela est un service Web, donc vous devez éviter de l’utiliser pour transformer des documents volumineux (le Service de Transformation dans BizTalk Server est mieux adapté pour les documents volumineux).  
  
> [!NOTE]
>  Par défaut, les services Web de la Transformation ne sont pas configurés pour exiger SSL Secure Sockets Layer () lors de l’accès par les clients. Vous devez configurer le service afin qu’il exige SSL pour l’accès client et protéger la connexion entre l’ordinateur hôte du service Web des Internet Information Services (IIS) et votre serveur BizTalk Server à l’aide d’IPSec d’au niveau du réseau et l’accès approprié au niveau des fichiers contrôler les autorisations de liste (ACL).