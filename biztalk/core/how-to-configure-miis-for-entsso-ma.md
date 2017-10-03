---
title: "Comment configurer MIIS pour l’agent de gestion ENTSSO | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7820384-ff64-4628-9e35-02b13803928f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 969a52beb02c3d2ba237369c16efec9ee84e2ef1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-miis-for-entsso-ma"></a>Configuration de MIIS pour l'agent de gestion de l'authentification unique de l'entreprise
Lorsque vous installez la fonctionnalité Administration de l'authentification unique de l'entreprise (que ce soit la version complète ou la version pour les administrateurs uniquement) sur un ordinateur exécutant MIIS (Microsoft Identity Integration Server), l'agent de gestion ENTSSO est installé automatiquement. Cela signifie que lorsque vous ouvrez MIIS, quasiment l'intégralité de la configuration a déjà été effectuée. La seule partie manquante concerne les informations de connexion.  
  
 Avant de commencer cette procédure, assurez-vous de disposer des informations suivantes :  
  
-   Le nom du serveur ENTSSO.  
  
-   L'ID utilisateur et le mot de passe du compte Windows sous lequel l'agent de gestion ENTSSO communique avec le serveur SSO.  
  
### <a name="to-configure-the-management-agent-within-miis"></a>Pour configurer l'agent de gestion dans MIIS  
  
1.  Ouvrez MIIS, puis ouvrez le **Identity Manager**.  
  
2.  Ouvrez le **créer un Agent de gestion** boîte de dialogue.  
  
3.  Sélectionnez **Enterprise Single Sign-On** dans la liste.  
  
     Cela démarre le **Assistant Création de l’Agent de gestion**.  
  
4.  Sur le **configurer les informations de connexion** page, dans le **se connecter à :** , entrez le nom du serveur SSO.  
  
5.  Entrez le nom de l'agent de gestion ENTSSO. Ce nom doit correspondre à celui spécifié dans le fichier ENTSSO.xml.  
  
6.  Dans le **utilisateur** champ, spécifiez le compte de domaine que l’Agent de gestion ENTSSO utilise pour gérer les mappages dans la base de données SSO.  
  
     Dans le système SSO, ce compte doit être membre du compte Administrateurs d'applications associées à authentification unique ou du compte Administrateurs de l'authentification unique.  
  
7.  Dans le **mot de passe** , entrez le mot de passe pour cet utilisateur.  
  
8.  Cliquez sur **suivant**, en acceptant les valeurs par défaut jusqu'à ce que vous atteigniez le **configurer des Extensions** page.  
  
9. Près de **les informations de connexion** pour l’extension de mot de passe, cliquez sur **paramètres**.  
  
     Le **paramètres de connexion** boîte de dialogue s’affiche.  
  
10. Dans le **se connecter à** , entrez le compte approprié. Ce compte doit être le même que le compte de service pour le service ENTSSO exécuté sur l'ordinateur spécifié.  
  
11. Dans le **utilisateur** et **mot de passe** , saisissez le nom d’utilisateur et un mot de passe pour le compte.  
  
12. Cliquez sur **OK**.  
  
13. Dans le **Agent de gestion MIISCreate**, cliquez sur **Terminer**.  
  
14. Toujours dans le **Identity Manager**, cliquez sur le **outils** menu, puis sur **Options**.  
  
     Le **Options** boîte de dialogue s’affiche.  
  
15. Sélectionnez **activer l’extension de règles du métaverse**.  
  
16. Dans le **le champ de nom d’extension des règles**, entrez **Microsoft.EnterpriseSingleSignOn.ManagementAgent.dll**.  
  
17. Cliquez sur **OK** puis fermez MIIS.  
  
## <a name="see-also"></a>Voir aussi  
 [L’utilisation de l’Agent de gestion ENTSSO](../core/how-to-use-the-entsso-management-agent.md)