---
title: "L’ajout d’un Port Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web ports, creating
- creating, Web ports
ms.assetid: da94d98e-10ca-437a-ba34-7aa6efc68f3d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42e9853755788aa29d3ca7506829dcd6bdfed53d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-web-port"></a>Ajout d'un port Web
L'ajout d'un port Web sur la surface d'un port s'effectue dans le Concepteur d'orchestration. Contrairement aux autres ports configurés, les ports Web prennent en charge une combinaison d'opérations de requête (unidirectionnelles) et de requête-réponse (bidirectionnelles). Chaque opération au niveau du port Web représente une méthode Web. Si la méthode Web contient *d’entrée* et *sortie* paramètres, BizTalk crée une opération de demande/réponse. Si le service Web contient uniquement un *d’entrée* paramètre, BizTalk crée uniquement une opération unidirectionnelle.  
  
### <a name="to-add-a-web-port"></a>Pour ajouter un port Web  
  
1.  Dans le Concepteur d’Orchestration, avec une orchestration est ouverte, cliquez sur la surface du port, puis sélectionnez **nouveau Port configuré**.  
  
2.  Dans la page **Bienvenue dans l'Assistant Configuration du port** , cliquez sur **Suivant**.  
  
3.  Sur le **propriétés de Port** page, dans le **nom** zone de texte, tapez un nom pour le port, puis cliquez sur **suivant**.  
  
4.  Dans le **sélectionner un Type de Port** , sélectionnez **utiliser un Type de Port existant**.  
  
5.  Dans le **Types de ports disponibles** , développez le **Types de ports Web** nœud et sélectionnez le site Web type qui correspond au service Web ajouté de port, puis cliquez sur **suivant**.  
  
     L’illustration suivante montre le **sélectionner un Type de Port** boîte de dialogue.  
  
     ![](../core/media/ebiz-prog-ws-addwebport.gif "ebiz_prog_ws_addwebport")  
  
6.  Dans le **liaison de Port** page, dans le **liaison de Port** liste déroulante, sélectionnez **spécifier maintenant**. BizTalk place automatiquement les valeurs du service Web référencé dans l'URI, le transport et le pipeline d'envoi et de réception. Il exploite ces valeurs pour créer le port d'envoi lors du déploiement de votre projet BizTalk.  
  
    > [!IMPORTANT]
    >  La méthode d'authentification par défaut pour le port d'envoi est l'authentification anonyme. Si un service Web demande une autre méthode d'authentification ou de chiffrement, vous devez modifier la configuration de manière à fournir les informations d'identification utilisateur appropriées ou utiliser SSL (Secure Sockets Layer) pour exécuter les services Web. Pour plus d’informations, consultez [: adaptateur d’envoi SOAP](../core/soap-send-adapter.md) et [exemple TMA : adaptateurs HTTP et SOAP](../core/sample-tma-http-and-soap-adapters.md).  
  
7.  Cliquez sur **suivant**, puis **Terminer** pour terminer l’Assistant.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment exécuter l’Assistant Configuration du Port](../core/how-to-run-the-port-configuration-wizard.md)   
 [Création de Ports Web](../core/creating-web-ports.md)