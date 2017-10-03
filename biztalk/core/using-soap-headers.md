---
title: "Utilisation des en-têtes SOAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP headers
- SOAP headers, about SOAP headers
- Web services, SOAP headers
ms.assetid: 816618ff-ecd8-4f12-b9a9-dbe4203411d8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0671dabe7547d3f55b937a1de58241a35cb70b39
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-soap-headers"></a>Utilisation des en-têtes SOAP
Microsoft BizTalk Server prend en charge les en-têtes SOAP définis et inconnus. Les en-têtes SOAP définis sont des en-têtes du fichier WSDL (Web Service Description Language) qui sont explicitement indiqués dans le service Web. Les en-têtes SOAP inconnus sont des en-têtes du fichier WSDL qui ne sont pas explicitement indiqués dans le service Web. Pour plus d’informations sur l’utilisation des en-têtes SOAP, consultez « Using SOAP Headers » dans la documentation de Microsoft .NET Framework à [http://go.microsoft.com/fwlink/?LinkId=25363](http://go.microsoft.com/fwlink/?LinkId=25363).  
  
 BizTalk Server crée une propriété de contexte pour chaque en-tête SOAP défini dans le service Web.  
  
> [!NOTE]
>  Les services Web utilisés prennent uniquement en charge les en-têtes SOAP définis. Vous ne pouvez pas définir d'en-têtes inconnus lors de l'utilisation de services Web.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [En-têtes SOAP avec les Services Web utilisés](../core/soap-headers-with-consumed-web-services.md)  
  
-   [En-têtes SOAP avec les Services Web publiés](../core/soap-headers-with-published-web-services.md)