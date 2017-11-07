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
ms.openlocfilehash: d6356a130b412ea849c79213ab55b000ea827f3a
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-configure-the-http-receive-adapter"></a>Comment faire pour configurer l’adaptateur de réception HTTP
L'adaptateur de réception HTTP permet d'envoyer des messages à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cet adaptateur est une extension ISAPI IIS (Internet Information Services) hébergée dans le processus IIS.  
  
### <a name="to-configure-the-http-receive-adapter"></a>Pour configurer l'adaptateur de réception HTTP  
  
1.  Copiez la réception HTTP (BTSHTTPReceive.dll) de l’adaptateur à partir de  **\<BizTalk > \HttpReceive >** vers le dossier qui contient votre projet Single Sign-On (SSO), par exemple :  
  
     **< Adapter_install > \biztalk\SSO\mySSODemo**  
  
    1.  Ajoutez une nouvelle extension de service Web mySSODemo.  
  
    2.  Localisez et copiez **< BizTalk_install > \HttpReceive** dans le dossier qui contient votre projet d’authentification unique, par exemple :  
  
         **< Adapter_install > \biztalk\SSO\mySSODemo\BTSHTTPReceive.dll.**  
  
    3.  Définir l’état de l’extension du service Web mySSODemo à **autorisées**.  
  
2.  Redémarrez IIS pour appliquer les modifications.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécuriser l’adaptateur](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)