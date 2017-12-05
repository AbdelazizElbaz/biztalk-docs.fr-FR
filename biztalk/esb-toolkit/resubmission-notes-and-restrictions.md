---
title: Les Restrictions et les Notes de la nouvelle soumission | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 391064a9-1d61-4b10-97ab-d93b37d1ae23
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d03c969dc056e251d8109ce5bc0a29c16f8ffeda
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="resubmission-notes-and-restrictions"></a><span data-ttu-id="0bc5a-102">Nouvelle soumission Remarques et Restrictions</span><span class="sxs-lookup"><span data-stu-id="0bc5a-102">Resubmission Notes and Restrictions</span></span>
<span data-ttu-id="0bc5a-103">Les notes et les restrictions suivantes s’appliquent au processus renvoyés :</span><span class="sxs-lookup"><span data-stu-id="0bc5a-103">The following notes and restrictions apply to the resubmission process:</span></span>  
  
-   <span data-ttu-id="0bc5a-104">Vous pouvez renvoyer des messages XML à l’ESB WCF rampe d’entrée, SOAP (ASMX) rampe d’entrée, ou emplacement de réception n’importe quel HTTP.</span><span class="sxs-lookup"><span data-stu-id="0bc5a-104">You can resubmit XML messages to the ESB WCF on-ramp, SOAP (ASMX) on-ramp, or any HTTP receive location.</span></span>  
  
-   <span data-ttu-id="0bc5a-105">L’URL par défaut de WCF rampe est http://localhost/ESB.ItineraryServices.WCF/ProcessItinerary.svc.</span><span class="sxs-lookup"><span data-stu-id="0bc5a-105">The default URL for the WCF on-ramp is http://localhost/ESB.ItineraryServices.WCF/ProcessItinerary.svc.</span></span>  
  
-   <span data-ttu-id="0bc5a-106">Le fichier Web.config du portail définit les détails de point de terminaison pour le WCF rampe d’entrée dans le  **\<Client\>**  nœud de la  **\<System.ServiceModel\>**  section.</span><span class="sxs-lookup"><span data-stu-id="0bc5a-106">The portal Web.config file defines the endpoint details for the WCF on-ramp in the **\<Client\>** node of the **\<System.ServiceModel\>** section.</span></span> <span data-ttu-id="0bc5a-107">Voici la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="0bc5a-107">The following is the default value.</span></span>  
  
    ```  
    <endpoint  
      address="http://localhost/ESB.ItineraryServices.WCF/ProcessItinerary.svc"  
      binding="wsHttpBinding"  
      bindingConfiguration="WSHttpBinding_ITwoWayAsyncVoid"  
      contract="ProcessRequest"   
      name="WSHttpBinding_ITwoWayAsyncVoid">                  
    </endpoint>  
    ```  
  
-   <span data-ttu-id="0bc5a-108">Si WCF rampe réside sur un serveur distant, vous devez mettre à jour l’adresse pour pointer vers le serveur approprié.</span><span class="sxs-lookup"><span data-stu-id="0bc5a-108">If the WCF on-ramp resides on a remote server, you must update the address to point to the correct server.</span></span>  
  
-   <span data-ttu-id="0bc5a-109">L’URL par défaut pour le SOAP (ASMX) rampe d’entrée est http://localhost/ESB.ItineraryServices/ProcessItinerary.asmx.</span><span class="sxs-lookup"><span data-stu-id="0bc5a-109">The default URL for the SOAP (ASMX) on-ramp is http://localhost/ESB.ItineraryServices/ProcessItinerary.asmx.</span></span>  
  
-   <span data-ttu-id="0bc5a-110">Le fichier Web.config du portail définit la configuration pour le SOAP (ASMX) rampe d’entrée dans le  **\<applicationSettings\>**  section.</span><span class="sxs-lookup"><span data-stu-id="0bc5a-110">The portal Web.config file defines the configuration for the SOAP (ASMX) on-ramp in the **\<applicationSettings\>** section.</span></span> <span data-ttu-id="0bc5a-111">Voici la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="0bc5a-111">The following is the default value.</span></span>  
  
    ```  
    <setting   
      name="Microsoft_Practices_ESB_Portal_ProcessItinerary_Process"  
      serializeAs="String">  
      <value>  
        http://localhost/ESB.ItineraryServices/ProcessItinerary.asmx  
      </value>  
    </setting>  
    ```  
  
-   <span data-ttu-id="0bc5a-112">Si ASMX rampe réside sur un serveur distant, vous devez mettre à jour l’URL avec l’adresse de serveur correct.</span><span class="sxs-lookup"><span data-stu-id="0bc5a-112">If the ASMX on-ramp resides on a remote server, you need to update the URL with the correct server address.</span></span>  
  
-   <span data-ttu-id="0bc5a-113">Vous pouvez soumettre à nouveau fichier plat emplacement de réception des messages mis en forme uniquement à HTTP.</span><span class="sxs-lookup"><span data-stu-id="0bc5a-113">You can resubmit flat file formatted messages only to an HTTP receive location.</span></span> <span data-ttu-id="0bc5a-114">Vous ne pouvez pas les envoyer à un WCF ou SOAP rampe d’entrée.</span><span class="sxs-lookup"><span data-stu-id="0bc5a-114">You cannot submit them to a WCF or SOAP on-ramp.</span></span> <span data-ttu-id="0bc5a-115">Vous devez vous assurer que le protocole HTTP emplacement de réception a le pipeline approprié qui peut consommer et/ou analyser le fichier plat.</span><span class="sxs-lookup"><span data-stu-id="0bc5a-115">You must ensure that the HTTP receive location has the appropriate pipeline that can consume and/or parse the flat file.</span></span>  
  
-   <span data-ttu-id="0bc5a-116">Le message soumise à nouveau ne contient pas toutes les propriétés de contexte du message d’origine.</span><span class="sxs-lookup"><span data-stu-id="0bc5a-116">The resubmitted message does not contain any of the context properties of the original message.</span></span>  
  
-   <span data-ttu-id="0bc5a-117">Nouvelle soumission s’applique à uniquement le corps du message ; Il ne s’applique pas à la totalité du message.</span><span class="sxs-lookup"><span data-stu-id="0bc5a-117">Resubmission applies to only the message body; it does not apply to the entire message.</span></span>  
  
-   <span data-ttu-id="0bc5a-118">Le processus de nouvelle soumission prend en charge uniquement les messages en une seule partie.</span><span class="sxs-lookup"><span data-stu-id="0bc5a-118">The resubmission process supports only single-part messages.</span></span> <span data-ttu-id="0bc5a-119">Vous ne pouvez pas utiliser le processus de nouvelle soumission avec des messages à parties multiples.</span><span class="sxs-lookup"><span data-stu-id="0bc5a-119">You cannot use the resubmission process with multi-part messages.</span></span>  
  
-   <span data-ttu-id="0bc5a-120">Vous ne peut pas renvoyer des messages au format binaire.</span><span class="sxs-lookup"><span data-stu-id="0bc5a-120">You cannot resubmit binary-formatted messages.</span></span>