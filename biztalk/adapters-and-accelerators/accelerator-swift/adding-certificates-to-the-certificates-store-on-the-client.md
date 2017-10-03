---
title: Ajout de certificats dans le magasin de certificats sur le Client | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, adding to certificates store
- certificates store
ms.assetid: 9e2722ee-dd6f-4b14-9796-2f2157e8cad2
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48a2e01fa60eccc8a6a0f06f4cf1f9fafb3f982b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adding-certificates-to-the-certificates-store-on-the-client"></a>Ajout de certificats dans le magasin de certificats sur le Client
Utilisez les étapes suivantes pour ajouter des certificats dans le dossier personnel dans le magasin de certificats sur chaque ordinateur client. Les certificats doivent être ajoutés dans le dossier personnel dans les certificats - magasin de l’utilisateur actuel.  
  
> [!IMPORTANT]
>  Si vos certificats ne sont pas distribués via une entreprise approuvé l’autorité de Certification, vous devez importer le certificat racine de l’autorité de Certification sur l’ordinateur client. Dans le cas contraire, vos certificats personnels ne fonctionnera pas. Importez le certificat de l’autorité de Certification dans le dossier autorités de Certification racines de confiance dans le nœud certificats (ordinateur Local).  
  
### <a name="to-add-certificates-to-the-certificate-store"></a>Pour ajouter des certificats au magasin de certificats  
  
1.  Cliquez sur **Démarrer**, puis sur **Exécuter**. Entrez **mmc**, puis cliquez sur **OK**.  
  
2.  Dans la boîte de dialogue Console1, cliquez sur **fichier**, puis cliquez sur **ajouter/supprimer un composant logiciel enfichable**.  
  
3.  Dans la boîte de dialogue Ajouter/supprimer un composant logiciel enfichable, cliquez sur **ajouter**.  
  
4.  Dans la boîte de dialogue Ajouter Standalone Snap-in, cliquez sur **certificats**, puis cliquez sur **ajouter**.  
  
5.  Dans la boîte de dialogue composant logiciel enfichable Certificats, cliquez sur **mon compte d’utilisateur**, puis cliquez sur **Terminer**.  
  
6.  Dans la boîte de dialogue Ajouter Standalone Snap-in, cliquez sur **certificats**, puis cliquez sur **ajouter**.  
  
7.  Dans la boîte de dialogue composant logiciel enfichable Certificats, cliquez sur **compte d’ordinateur**, puis cliquez sur **suivant**.  
  
8.  Dans la boîte de dialogue Sélectionner un ordinateur, assurez-vous que **ordinateur Local** est sélectionné, puis cliquez sur **Terminer**.  
  
9. Dans la boîte de dialogue Ajouter Standalone Snap-in, cliquez sur **fermer**.  
  
10. Dans la boîte de dialogue Ajouter/supprimer un composant logiciel enfichable, cliquez sur **OK**.  
  
11. Dans le **racine de la Console** volet de la boîte de dialogue Console1, développez le **certificats - utilisateur actuel** dossiers.  
  
12. Sous **certificats - utilisateur actuel**, développez **personnel**.  
  
13. Avec le bouton droit **certificats**, pointez sur **toutes les tâches**, puis cliquez sur **importation**.  
  
14. Dans la page d’accueil de l’Assistant Importation de certificat, cliquez sur **suivant**.  
  
15. Dans la page fichier à importer, cliquez sur **Parcourir**.  
  
16. Dans la boîte de dialogue Ouvrir, déplacer vers l’emplacement du fichier où vous avez enregistré votre certificat, sélectionnez **tous les fichiers** pour **types de fichiers**, sélectionnez le certificat que vous souhaitez importer, puis cliquez sur  **Ouvrez**.  
  
17. Dans la page fichier à importer, cliquez sur **suivant**.  
  
18. Dans la page magasin de certificats, vérifiez que **placer tous les certificats dans le magasin suivant** est sélectionnée, vérifiez que **personnel** s’affiche dans le **magasin de certificats** zone, puis cliquez sur **suivant**.  
  
19. Sur la fin de la page de l’Assistant Importation de certificat, cliquez sur **Terminer**.  
  
20. Dans la boîte de dialogue Assistant Importation de certificat indiquant une importation réussie, cliquez sur **OK**.  
  
21. Répétez les étapes 13 à 20 pour tous les autres certificats que vous allez utiliser dans le message repair et new submission.