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
ms.openlocfilehash: 194306da3b021e7460b88a3d8e76801a2eeaebba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-throwdetailederror-switch"></a>L’utilisation du commutateur ThrowDetailedError
Si une erreur se produit, le client Web reçoit un générique **SoapException**.  
  
 Pour déboguer votre service Web publié, vous pouvez ajouter un commutateur au fichier web.config pour contrôler le niveau de détails de l'exception renvoyée par le service Web publié.  
  
 Le fichier Web.config contient un commutateur de paramètre d’application, **ThrowDetailedError**. **False** est la valeur par défaut **ThrowDetailedError**. Si vous modifiez le paramètre pour **True**, le serveur proxy retourne des informations sur l’exception interne au client Web, ce qui vous permet de déboguer le service Web publié.  
  
 Le code XML suivant montre la **ThrowDetailedError** commutateur qui apparaît dans le fichier Web.config sous le \<appSettings > nœud :  
  
```  
<appSettings>  
  <add key="ThrowDetailedError" value="False" />  
<appSettings/>  
```  
  
> [!IMPORTANT]
>  Par défaut, BizTalk Server ne renvoie pas d'informations sur l'exception interne au client Web car celles-ci peuvent contenir des informations personnelles, telles que les piles d'appels de l'application. Après le débogage, vous devez définir le **ThrowDetailedError** à **False**.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage de Services Web publiés](../core/debugging-published-web-services.md)