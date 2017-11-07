---
title: "Configurer la réception HTTP 2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP receive adapter, configuring
- configuring HTTP receive adapter
ms.assetid: dd26fd57-90d8-4ffe-b56f-8de55ecc6f68
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed6e40036308aa872a2d6ba23da8209ee9f80cfc
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-configure-the-http-receive-adapter"></a>Comment faire pour configurer l’adaptateur de réception HTTP
Vous pouvez utiliser l'adaptateur de réception HTTP pour envoyer les messages à BizTalk Server. Cet adaptateur est une extension ISAPI IIS (Internet Information Services) hébergée dans le processus IIS.  
  
### <a name="to-configure-the-http-receive-adapter"></a>Pour configurer l'adaptateur de réception HTTP  
  
1.  Copiez la réception HTTP (BTSHTTPReceive.dll) de l’adaptateur à partir de  **\<BizTalk2010 > \HttpReceive >** au dossier contenant votre projet Single Sign-On (SSO) (par exemple, **< Adapter_install > \ biztalk2010\SSO\mySSODemo**).  
  
    1.  Ajoutez une nouvelle extension de service Web mySSODemo.  
  
    2.  Accédez au fichier <BizTalk_install>\HttpReceive et copiez-le dans le dossier contenant votre projet d'authentification unique (par exemple,  
  
         <Installation_adaptateur>\biztalk2010\SSO\mySSODemo\BTSHTTPReceive.dll.  
  
    3.  Définir le statut de l’extension du service Web mySSODemo à **autorisées**.  
  
2.  Redémarrez IIS pour que ces modifications prennent effet.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité de la carte](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)