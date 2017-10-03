---
title: "SOAP des paramètres de réglage et de Configuration de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [SOAP adapters], tuning
- SOAP adapters, tuning
ms.assetid: 73c175aa-16b9-4620-b303-9092ae29af21
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be6a71938876ad932a58d369abe40d7c8b073f72
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="soap-adapter-configuration-and-tuning-parameters"></a>Paramètres de configuration et de réglage de l'adaptateur SOAP
Vous pouvez configurer le nombre de connexions simultanées ouvertes par l'adaptateur SOAP pour un serveur de destination particulier en créant une entrée dans le fichier BTSNTSvc.exe.config situé dans le répertoire d'installation BizTalk Server racine.  
  
> [!NOTE]
>  Cette propriété est appliquée aux adaptateurs HTTP et SOAP s'ils envoient des messages au même serveur HTTP de destination. La valeur par défaut de la propriété « maxconnexion » est 2. La valeur maximale qui peut être définie pour la propriété « maxconnexion » pour tous les URI est 20.  
  
 Voici un exemple de configuration de la propriété du nombre maximal de connexions :  
  
```  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "20" />  
      <add address = "http://www.northwind.com" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur SOAP](../core/configuring-the-soap-adapter.md)   
 [Paramètres de réglage et de Configuration de l’adaptateur HTTP](../core/http-adapter-configuration-and-tuning-parameters.md)