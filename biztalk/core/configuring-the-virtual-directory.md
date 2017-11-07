---
title: "Configuration du répertoire virtuel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- virtual directory, configuring
- configuring virtual directory
ms.assetid: 548e3bee-66bc-424c-895d-e8672a3d6301
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5e74e297eba5dcc92d2008bcca90fdc7b325814
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="configuring-the-virtual-directory"></a>Configuration du répertoire virtuel
Cette rubrique indique les procédures de configuration du répertoire virtuel et la vérification de l’application pour un utilisateur.  
  
## <a name="configuring-the-directory"></a>Configuration du répertoire  
  
#### <a name="to-configure-the-virtual-directory"></a>Pour configurer le répertoire virtuel  
  
1.  Sur le lecteur système (%systemdrive%), créez un dossier à configurer en tant que répertoire virtuel.  
  
2.  Cliquez sur **Démarrer**, pointez sur **programmes**, cliquez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
3.  Développez  **\<nom du serveur >** , puis **Sites**.  
  
4.  Avec le bouton droit **Site Web par défaut** et cliquez sur **ajouter un répertoire virtuel**.  
  
5.  Dans le **ajouter un répertoire virtuel** boîte de dialogue, tapez l’alias.  
  
6.  Tapez le chemin d'accès au dossier créé à l'étape 1. Sinon, cliquez sur **(...)**  pour accéder à l’emplacement du dossier.  
  
7.  Cliquez sur **OK**. Le dossier s’affiche sous le **Site Web par défaut** dossier.  
  
8.  Cliquez avec le bouton droit et cliquez sur **convertir en Application**.  
  
9. Dans le **ajouter une Application** boîte de dialogue, cliquez sur **OK**. Le dossier est converti en application (l'icône de dossier devient une icône de site Web).  
  
## <a name="verifying-an-application-for-a-user"></a>Vérification d'une application pour un utilisateur  
 Les applications IIS sont exécutées à un niveau d'isolation élevé. Aussi, vous devez vérifier que l'application peut être exécutée dans le contexte d'un utilisateur dans le groupe Utilisateurs d'hôtes BizTalk isolés à l'aide de la procédure suivante.  
  
#### <a name="to-verify-an-application-for-a-user"></a>Pour vérifier une application pour un utilisateur  
  
1.  Dans le panneau de configuration, ouvrez **outils d’administration**, puis cliquez sur **Services de composants**.  
  
2.  Accédez à l’application COM + dans **Services de composants**.  
  
3.  Cliquez sur l’application COM +, puis cliquez sur **propriétés**.  
  
4.  Cliquez sur **identifier** et modifier l’identité sous laquelle cette application COM + s’exécute à un utilisateur qui est membre d’un groupe BizTalk Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité de la carte](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)