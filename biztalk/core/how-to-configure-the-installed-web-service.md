---
title: "Comment configurer le Service Web installé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web services, configuring
- deploying, Web services
- Web services, deploying
ms.assetid: 5a281daa-9e1c-47b0-9002-66ea18ed6caf
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f54d5fd99bfa9f5a7440202848c4d43259d0a42
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-installed-web-service"></a>Configuration du service Web installé
Après avoir installé les fichiers du service Web, vous devez configurer BizTalk Server de sorte qu'il reçoive des messages en provenance du service Web.  
  
### <a name="to-configure-the-web-service"></a>Pour configurer le service Web  
  
1.  Dans la console Administration de BizTalk Server, développez **groupe BizTalk**, développez **Applications**, puis cliquez sur l’application que vous souhaitez configurer le Service Web.  
  
2.  Pointez sur **importation**, puis cliquez sur **liaisons**.  
  
3.  Sélectionnez le fichier BindingInfo.xml dans le dossier de distribution, puis cliquez sur **OK**.  
  
4.  Démarrez les orchestrations et activez les emplacements de réception.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment importer des liaisons dans une Application BizTalk](../core/how-to-import-bindings-into-a-biztalk-application.md)   
 [Déploiement de Services Web publiés sur un ordinateur Non-Visual Studio](../core/deploying-published-web-services-on-a-non-visual-studio-computer.md)