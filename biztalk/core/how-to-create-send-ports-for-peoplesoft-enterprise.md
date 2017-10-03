---
title: "Comment créer des Ports d’envoi pour PeopleSoft Enterprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating send ports
- send ports, creating
ms.assetid: 374261ce-2cb5-4193-a0a2-658f989b2c60
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b6b5caa44976aec7a4afb8e0eccf5b1f8904111
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-send-ports-for-peoplesoft-enterprise"></a>Création des ports d'envoi pour PeopleSoft Enterprise
Suivez les étapes ci-après pour créer un port d'envoi à l'aide de la console Administration de BizTalk Server.  
  
## <a name="creating-a-send-port"></a>Création d'un port d'envoi  
  
#### <a name="to-create-a-send-port"></a>Pour créer un port d’envoi  
  
1.  Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.  
  
2.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :  
  
    1.  Tapez un nom pour le port d’envoi, par exemple, `SSOSendToPeopleSoft`.  
  
    2.  À partir de la **Type** la liste déroulante, sélectionnez **PeopleSoft**.  
  
    3.  À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.  
  
    4.  Dans la liste déroulante Pipeline d’envoi, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.  
  
    5.  À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.  
  
    6.  Cliquez sur **configurer** pour configurer le port d’envoi.  
  
4.  Dans le **propriétés du Transport PeopleSoft** boîte de dialogue zone, procédez comme suit :  
  
    1.  Développez **propriétés obligatoires de l’adaptateur**, puis entrez **chemin d’accès au serveur d’Application**, **JAVA_HOME**, **nom d’utilisateur**,  **mot de passe**et le fichier Jar pour la connexion au système Peoplesoft.  
  
         Il n'est pas nécessaire de définir les informations de connexion.  
  
    2.  Dans la liste, sélectionnez l'application associée SSO que vous avez créée pour représenter le système PeopleSoft.  
  
    3.  Pour **utiliser SSO**, sélectionnez **Oui**.  
  
    4.  Cliquez sur **OK**.  
  
5.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de gestionnaires d’envoi PeopleSoft](../core/creating-peoplesoft-send-handlers.md)