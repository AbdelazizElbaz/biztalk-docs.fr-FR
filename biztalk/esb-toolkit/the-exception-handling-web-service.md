---
title: Le Service Web de gestion des exceptions | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfe6ebdf-9b92-40c7-93fb-afd6c5f68aaa
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb8d8f3439e3b99d118e2932d0a158113ec51be2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-exception-handling-web-service"></a>Le Service Web de gestion des exceptions
Le service Web de gestion des exceptions accepte un message d’erreur et le publie dans le portail d’Exception ESB. Une application cliente peut créer des messages d’exception et les envoyer à l’architecture ESB, où tout gestionnaire configuré pour ce type d’exception ou un gestionnaire générique, peut traiter l’exception. Le principal avantage de ce service est qu’il permet d’entités en dehors d’une application ESB devant être inclus dans le mécanisme de gestion des exceptions de ESB.  
  
 Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] contient deux versions de ce service : une version de ASP.NET (ASMX) et une version de Windows Communication Foundation (WCF). Les noms de service sont **ESB. ExceptionHandlingServices** et **ESB. ExceptionHandlingServices.WCF**, respectivement, et les services exposent une méthode unique :  
  
-   **SubmitFault**. Cette méthode prend une instance de la **FaultMessage** classe et n’a aucune valeur de retour.  
  
 Pour plus d’informations sur la façon dont le mécanisme de gestion des exceptions fonctionnement, consultez [à l’aide de gestion des exceptions ESB](../esb-toolkit/using-esb-exception-management.md).  
  
> [!NOTE]
>  Par défaut, les services Web de la gestion des exceptions ne sont pas configurés pour exiger SSL Secure Sockets Layer () lors de l’accès par les clients. Vous devez configurer le service afin qu’il exige SSL pour l’accès client et protéger la connexion entre l’ordinateur hôte du service Web des Internet Information Services (IIS) et le serveur qui héberge le **ESBExceptions** base de données à l’aide d’IPSec d’au niveau du réseau et les autorisations de liste (ACL) de contrôle de l’accès approprié au niveau du fichier.