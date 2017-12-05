---
title: "L’utilisation du commutateur ThrowDetailedError | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web services, security
- Web services, debugging
ms.assetid: 8a8af3c0-a9a2-42fe-b0be-a5a106403747
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90929015e2d1d0567af0ccc5c51c6aae450d49c8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-use-the-throwdetailederror-switch"></a><span data-ttu-id="02b65-102">L’utilisation du commutateur ThrowDetailedError</span><span class="sxs-lookup"><span data-stu-id="02b65-102">How to Use the ThrowDetailedError Switch</span></span>
<span data-ttu-id="02b65-103">Si une erreur se produit, le client Web reçoit un générique **SoapException**.</span><span class="sxs-lookup"><span data-stu-id="02b65-103">If an error occurs, the Web client receives a generic **SoapException**.</span></span>  
  
 <span data-ttu-id="02b65-104">Pour déboguer votre service Web publié, vous pouvez ajouter un commutateur au fichier web.config pour contrôler le niveau de détails de l'exception renvoyée par le service Web publié.</span><span class="sxs-lookup"><span data-stu-id="02b65-104">To debug your published Web service, you can add a switch to the Web.config file to control the level of the exception details returned from the published Web service.</span></span>  
  
 <span data-ttu-id="02b65-105">Le fichier Web.config contient un commutateur de paramètre d’application, **ThrowDetailedError**.</span><span class="sxs-lookup"><span data-stu-id="02b65-105">The Web.config file contains an application setting switch, **ThrowDetailedError**.</span></span> <span data-ttu-id="02b65-106">**False** est la valeur par défaut **ThrowDetailedError**.</span><span class="sxs-lookup"><span data-stu-id="02b65-106">**False** is the default setting for **ThrowDetailedError**.</span></span> <span data-ttu-id="02b65-107">Si vous modifiez le paramètre pour **True**, le serveur proxy retourne des informations sur l’exception interne au client Web, ce qui vous permet de déboguer le service Web publié.</span><span class="sxs-lookup"><span data-stu-id="02b65-107">If you change the setting to **True**, the server proxy returns inner exception information to the Web client enabling you to debug the published Web service.</span></span>  
  
 <span data-ttu-id="02b65-108">Le code XML suivant montre la **ThrowDetailedError** commutateur qui apparaît dans le fichier Web.config sous le \<appSettings\> nœud :</span><span class="sxs-lookup"><span data-stu-id="02b65-108">The following XML code shows the **ThrowDetailedError** switch that appears in the Web.config file under the \<appSettings\> node:</span></span>  
  
```  
<appSettings>  
  <add key="ThrowDetailedError" value="False" />  
<appSettings/>  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="02b65-109">Par défaut, BizTalk Server ne renvoie pas d'informations sur l'exception interne au client Web car celles-ci peuvent contenir des informations personnelles, telles que les piles d'appels de l'application.</span><span class="sxs-lookup"><span data-stu-id="02b65-109">BizTalk Server does not return inner exception information to the Web client by default since it may contain sensitive information, such as application call stacks.</span></span> <span data-ttu-id="02b65-110">Après le débogage, vous devez définir le **ThrowDetailedError** à **False**.</span><span class="sxs-lookup"><span data-stu-id="02b65-110">After debugging, you should set the **ThrowDetailedError** setting to **False**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02b65-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02b65-111">See Also</span></span>  
 [<span data-ttu-id="02b65-112">Débogage des services web publiés</span><span class="sxs-lookup"><span data-stu-id="02b65-112">Debugging Published Web Services</span></span>](../core/debugging-published-web-services.md)