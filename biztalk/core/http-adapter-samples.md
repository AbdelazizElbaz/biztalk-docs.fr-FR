---
title: "Exemples d’adaptateur HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP adapters, examples
- examples, HTTP adapters
ms.assetid: 6796ea39-2947-45df-b228-1ecdb23a7ab8
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1111322d59f8ff5c6ba6209aa48eb515a23c72f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="http-adapter-samples"></a>Exemples d'adaptateur HTTP
Cette section contient des exemples qui illustrent des fonctionnalités avancées lors de l'utilisation de l'adaptateur HTTP BizTalk.  
  
> [!NOTE]
>  Avant d'exécuter cet exemple, effectuez les étapes suivantes :  
>   
>  1.  Ouvrez IIS, ajoutez les restrictions ISAPI et CGI :  
>   
>      Cliquez sur Nom de l'ordinateur dans le volet gauche, puis sur Restrictions ISAPI et CGI dans le volet droit, puis ajoutez le chemin ISAPI ou CGI :  
>   
>      Sur un ordinateur 64 bits, ajoutez : C:\Program Files (x86) \Microsoft BizTalk Server \<version\>\HttpReceive64\BTSHTTPReceive.dll  
>   
>      Sur un ordinateur 32 bits, ajoutez : C:\Program Files (x86) \Microsoft BizTalk Server \<version\>\HttpReceive\BTSHTTPReceive.dll  
>   
>      Cochez le chemin de l'extension autorisé ou exécutez-le.  
> 2.  Cliquez sur HTTPRequestResponseSample dans le volet gauche, puis sur Mappage de gestionnaires dans le volet central, puis cliquez sur Ajouter un mappage de scripts avec les paramètres suivants :  
>   
>      Chemin des demandes : BTSHTTPReceive.dll  
>   
>      Exécutable :  
>   
>      Sur un ordinateur 64 bits, ajoutez : C:\Program Files (x86) \Microsoft BizTalk Server \<version\>\HttpReceive64\  
>   
>      Sur un ordinateur 32 bits, ajoutez : C:\Program Files (x86) \Microsoft BizTalk Server \<version\>\HttpReceive\  
>   
>      Restrictions des demandes :  
>   
>      Verbes : POST  
>   
>      Accès : Script  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [HTTPSolicitResponse](../core/httpsolicitresponse.md)  
  
-   [HTTPRequestResponse](../core/httprequestresponse.md)