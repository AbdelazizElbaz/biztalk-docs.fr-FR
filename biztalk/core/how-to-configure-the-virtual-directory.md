---
title: "Comment configurer le répertoire virtuel | Documents Microsoft"
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
- applications, verifying for users
- verifying applications for users
ms.assetid: 3da16524-8238-426a-88f8-434be5992e13
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b1461ac2ea0ef9cfee71965fc2cc800d617d1d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-virtual-directory"></a>Comment configurer le répertoire virtuel
Cette rubrique décrit les procédures de configuration du répertoire virtuel et de vérification de l'application pour un utilisateur.  
  
### <a name="to-configure-the-virtual-directory"></a>Pour configurer le répertoire virtuel  
  
1.  Sur le lecteur système (%systemdrive%), créez un dossier à configurer en tant que répertoire virtuel.  
  
2.  Cliquez sur **Démarrer**, pointez sur **programmes**, cliquez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
3.  Développez  **\<nom du serveur >** , puis **Sites**.  
  
4.  Avec le bouton droit **Site Web par défaut** et cliquez sur **ajouter un répertoire virtuel**.  
  
5.  Dans le **ajouter un répertoire virtuel** boîte de dialogue, tapez l’alias.  
  
6.  Tapez le chemin d'accès au dossier créé à l'étape 1. Sinon, cliquez sur **(...)**  pour accéder à l’emplacement du dossier.  
  
7.  Cliquez sur **OK**. Le dossier s’affiche sous le **Site Web par défaut** dossier.  
  
8.  Cliquez avec le bouton droit et cliquez sur **convertir en Application**.  
  
9. Dans le **ajouter une Application** boîte de dialogue, cliquez sur **OK**. Le dossier est converti en application (l'icône de dossier devient une icône de site Web).  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’authentification unique](../core/using-single-sign-on2.md)