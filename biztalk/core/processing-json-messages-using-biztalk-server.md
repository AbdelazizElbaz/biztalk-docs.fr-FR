---
title: "Traitement des messages JSON à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6db1421-9478-477c-8645-09eefba06246
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ea474e3717ec69dfe04261ba144a46350223856
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="processing-json-messages-using-biztalk-server"></a>Traitement des messages JSON à l'aide de BizTalk Server
> [!NOTE]
>  Ce didacticiel s'applique uniquement à [!INCLUDE[prague](../includes/prague-md.md)].  
  
 Ce didacticiel explique comment traiter les messages JSON à l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Le didacticiel utilise les composants de pipeline personnalisé maintenant disponibles avec [!INCLUDE[prague](../includes/prague-md.md)]. Ces composants de pipeline convertissent le message JSON en XML lors de la réception du message dans l'orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], et convertit le message du format XML au format JSON lors de l'envoi du message.  
  
## <a name="what-does-this-tutorial-do"></a>À quoi sert ce didacticiel ?  
 Pour illustrer le traitement JSON, nous créons une [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui effectue ce qui suit, dans l'ordre indiqué :  
  
1.  Reçoit un bon de commande JSON et, dans le pipeline de réception, utilise un composant du décodeur JSON pour transformer le message JSON en message XML.  
  
2.  Transforme le bon de commande XML en facture XML à l'aide d'un mappage.  
  
3.  Dans le pipeline d'envoi, utilise un encodeur JSON pour transformer la facture XML en une facture JSON et l'envoie.  
  
 ![Traitement des messages JSON dans BizTalk Server](../core/media/btsjson-flow.png "BTSJSON_Flow")  
  
## <a name="how-to-use-this-tutorial"></a>Comment utiliser ce didacticiel ?  
 Ce didacticiel est construit autour d’un exemple (**BTSJSON**) qui peut être téléchargé à partir de la [MSDN Code Gallery](http://go.microsoft.com/fwlink/?LinkId=403197). Vous pouvez utiliser l'exemple et parcourir ce didacticiel pour comprendre comment l'exemple a été construit. Vous pouvez également utiliser ce didacticiel pour créer votre propre solution de bout en bout. Ce didacticiel cible la seconde approche afin que vous compreniez comment cette solution a été construite. Dans toute la mesure du possible, ce didacticiel est également compatible avec l'exemple et utilise les mêmes noms des artefacts (par exemple, des schémas, des transformations) que ceux employés dans l'exemple.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Générer un schéma XSD pour un message JSON](../core/generate-an-xsd-schema-for-json-message.md)  
  
-   [Créer des pipelines personnalisés pour traiter les messages JSON](../core/create-custom-pipelines-to-process-json-messages.md)  
  
-   [Créer une orchestration BizTalk Server](../core/create-a-biztalk-server-orchestration.md)  
  
-   [Déployer et tester l’application](../core/deploy-and-test-the-application.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels de BizTalk Server](../core/biztalk-server-tutorials.md)