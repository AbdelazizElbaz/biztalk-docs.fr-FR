---
title: "Les Services Web de rampe d’entrée d’itinéraire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7551974-b9d2-4ae3-b54c-3aa5ba058e95
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36d3724a6cd57dca8157c05e95d9e196f0fb6cf8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-itinerary-on-ramp-web-services"></a>Les Services Web de rampe d’entrée d’itinéraire
Le service Web de l’itinéraire est une feuille de route rampe d’entrée qui expose une méthode qui permet aux clients d’envoyer des messages à traiter par le Service de l’itinéraire et puis ultérieur à la cible Microsoft BizTalk ou d’opérations d’ESB.  
  
 Le service Web de l’itinéraire transmet la charge utile pour les composants de pipeline ESB itinéraire, qui valide la feuille de route pour vérifier que ces services sont définis dans le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] configuration. Le composant ajoute alors les propriétés de contexte spéciale pour le message contenant la feuille de route validé.  
  
 Dans le cas d’un générique d’itinéraire rampe d’entrée, un en-tête SOAP contenant un itinéraire n’est pas fourni lors de l’envoi du message. En conséquence, le composant de pipeline ESB itinéraire sélecteur est utilisé à la place le composant de pipeline ESB itinéraire. Le composant de pipeline ESB itinéraire sélecteur résout l’itinéraire basé sur une chaîne de connexion du programme de résolution prédéfinis, et il fournit la même validation fournies par le composant de pipeline ESB itinéraire.  
  
 La [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] inclut deux variantes du service de feuille de route pour prendre en charge les deux unidirectionnel et modèles d’échange de messages de demande-réponse. Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] contient ASP.NET (ASMX) et une version de Windows Communication Foundation (WCF) de ces deux services, et fournit des versions génériques de services WCF.  
  
 Les noms des services d’itinéraire unidirectionnels fournis sont **ESB. ItineraryService**, **ESB. ItineraryServices.WCF**, et **ESB. ItineraryServices.Generic.WCF**.  
  
 Les noms des services d’itinéraire bidirectionnelles fournis sont **ESB. ItineraryServices.Response**, **ESB. ItineraryServices.Response.WCF**, et **ESB. ItineraryServices.Generic.Response.WCF**.  
  
 Chacun des services Web de l’itinéraire expose les méthodes suivantes :  
  
-   **SubmitRequest**. Pour le service basés sur ASMX, cette méthode prend une instance de la **XmlNode** classe qui contient le message à envoyer. Pour le service WCF, cette méthode prend une chaîne XML qui contient le message à envoyer.  
  
-   **SubmitRequestResponse**. Pour le service basés sur ASMX, cette méthode prend une référence à une instance de la **XmlNode** classe qui contient le message à envoyer et retourne le message de réponse de l’instance de la **XmlNode** transmis à Il s’agit. Pour le service WCF, cette méthode prend une référence à un **objet** type qui est une chaîne XML qui contient le message à envoyer et retourne un tableau de **XmlNodes** dans le **objet** qui a été passé.  
  
 Pour plus d’informations sur l’utilisation des services Web de la feuille de route, consultez [l’installation et l’exécution de l’exemple de rampe d’entrée d’itinéraire](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).  
  
> [!NOTE]
>  Par défaut, les services Web de l’itinéraire ne sont pas configurés pour exiger SSL Secure Sockets Layer () lors de l’accès par les clients. Vous devez configurer le service pour exiger SSL pour l’accès client et de protéger la connexion entre l’ordinateur hôte du service Web des Internet Information Services (IIS) et le serveur qui héberge la base de données ESBExceptions à l’aide d’un IPSec au niveau du réseau et appropriées autorisations de liste (ACL) de contrôle d’accès de niveau fichier