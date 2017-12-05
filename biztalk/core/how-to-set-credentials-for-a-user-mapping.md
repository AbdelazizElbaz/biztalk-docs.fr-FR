---
title: "Comment définir les informations d’identification d’un mappage utilisateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maps [SSO], credentials
- managing [SSO maps], configuring credentials
ms.assetid: 75b29114-56b6-4db0-8666-61cf6c675401
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4853499dbfd85cd5114212e37f4d22770d64a22
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-set-credentials-for-a-user-mapping"></a>Comment définir les informations d’identification d’un mappage utilisateur
Cette commande permet de définir les informations d’identification pour un utilisateur d’accéder à une application spécifique.  
  
 Cette commande n'affiche pas le mot de passe durant sa saisie.  
  
 Si le mappage utilisateur existe déjà, cette commande définit les informations d’identification pour le mappage existant. Si vous n'avez pas créé le mappage utilisateur, le système SSO vous invite à saisir l'ID de l'utilisateur pour l'application.  
  
### <a name="to-set-credentials-for-a-user-mapping"></a>Pour définir les informations d'identification d'un mappage utilisateur  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  **\<lecteur\>**: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage – setcredentials \<domaine\>\\< nom d’utilisateur\> \<applicationname\>**, où  **\< domaine\>**  correspond au domaine Windows pour le compte d’utilisateur,  **\<nom d’utilisateur\>**  est le nom d’utilisateur Windows et  **\<applicationname \>**  l’application spécifique pour lequel vous souhaitez définir les informations d’identification.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
4.  Lorsque vous y êtes invité, entrez le mot de passe d'utilisateur pour cette application.  
  
5.  Si vous n'avez pas créé le mappage utilisateur, le système SSO vous invite à saisir l'ID de l'utilisateur pour l'application.  
  
### <a name="to-set-credentials-for-a-user-mapping-from-the-client-utility"></a>Pour définir les informations d'identification d'un mappage utilisateur à partir de l'utilitaire client  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  **\<lecteur\>**: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssoclient - setcredentials \<nom de l’application\>**, où  **\<nom de l’application\>**  est le nom de l’application associée vous vous souhaitez supprimer le mappage utilisateur.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment créer des mappages utilisateur](../core/how-to-create-user-mappings.md)   
 [Mappages SSO](../core/sso-mappings.md)   
 [Gestion des Applications associées](../core/managing-affiliate-applications.md)   
 [Gestion des mappages utilisateur](../core/managing-user-mappings.md)