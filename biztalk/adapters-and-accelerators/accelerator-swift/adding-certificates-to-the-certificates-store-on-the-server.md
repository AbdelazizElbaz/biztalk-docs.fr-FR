---
title: Ajout de certificats dans le magasin de certificats sur le serveur | Documents Microsoft
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
ms.assetid: 075cfae8-dce7-46f7-9539-796f03229ea2
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94661568108e5a1cc05140a97c933fb8d00e3c67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adding-certificates-to-the-certificates-store-on-the-server"></a>Ajout de certificats dans le magasin de certificats sur le serveur
Utilisez les étapes suivantes pour ajouter des certificats dans le dossier d’autres personnes dans le magasin de certificats (ordinateur Local) sur l’ordinateur du serveur.  
  
### <a name="to-add-certificates-to-the-certificate-store"></a>Pour ajouter des certificats au magasin de certificats  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk Accelerator pour SWIFT**, puis cliquez sur **BizTalk Accelerator pour SWIFT gestion Console**.  
  
    > [!NOTE]
    >  Si la fenêtre MMC est toujours ouvert à partir de la procédure précédente (ajout de certificats dans le magasin de certificats sur le Client), vous pouvez l’utiliser pour cette procédure.  
  
2.  Dans la fenêtre de la Console d’Administration, développez le **certificats (ordinateur Local)** dossier, puis développez **autres personnes**.  
  
3.  Avec le bouton droit **certificats**, pointez sur **toutes les tâches**, puis cliquez sur **importation**.  
  
4.  Dans la page d’accueil de l’Assistant Importation de certificat, cliquez sur **suivant**.  
  
5.  Dans la page fichier à importer, cliquez sur **Parcourir**.  
  
6.  Dans la boîte de dialogue Ouvrir, déplacer vers l’emplacement du fichier où vous avez enregistré votre certificat, sélectionnez **tous les fichiers** pour **types de fichiers**, sélectionnez le certificat que vous souhaitez importer, puis cliquez sur  **Ouvrez**.  
  
7.  Dans la page fichier à importer, cliquez sur **suivant**.  
  
8.  Dans la page magasin de certificats, vérifiez que **placer tous les certificats dans le magasin suivant** est sélectionnée, vérifiez que **autres personnes** s’affiche dans le **le magasin de certificats**zone, puis cliquez sur **suivant**.  
  
9. Sur la fin de la page de l’Assistant Importation de certificat, cliquez sur **Terminer**.  
  
10. Dans la boîte de dialogue Assistant Importation de certificat indiquant une importation réussie, cliquez sur **OK**.  
  
11. Répétez les étapes 3 à 10 pour tous les autres certificats que vous allez utiliser dans le message repair et new submission.