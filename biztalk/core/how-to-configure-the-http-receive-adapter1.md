---
title: "Configurer la réception HTTP 1 | Documents Microsoft"
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
ms.assetid: e7dbfed3-9dd8-49c9-90b6-a655d7c5446f
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c18cdcad8deaa9cd76930b91e94860c99749f78
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-configure-the-http-receive-adapter"></a>Comment faire pour configurer l’adaptateur de réception HTTP
L'adaptateur de réception HTTP permet d'envoyer des messages à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cet adaptateur est une extension ISAPI IIS (Internet Information Services) hébergée dans le processus IIS.  
  
### <a name="to-configure-the-http-receive-adapter"></a>Pour configurer l'adaptateur de réception HTTP  
  
1.  Copiez la réception HTTP (BTSHTTPReceive.dll) de l’adaptateur à partir de  **\<BizTalk\>\HttpReceive\>**  dans le dossier qui contient votre projet Single Sign-On (SSO), par exemple :  
  
     **<Adapter_install>\biztalk\SSO\mySSODemo**  
  
    1.  Ajoutez une nouvelle extension de service Web mySSODemo.  
  
    2.  Localisez et copiez **< BizTalk_install > \HttpReceive** dans le dossier qui contient votre projet d’authentification unique, par exemple :  
  
         **<Adapter_install>\biztalk\SSO\mySSODemo\BTSHTTPReceive.dll.**  
  
    3.  Définir l’état de l’extension du service Web mySSODemo à **autorisées**.  
  
2.  Redémarrez IIS pour appliquer les modifications.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécuriser l’adaptateur](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)