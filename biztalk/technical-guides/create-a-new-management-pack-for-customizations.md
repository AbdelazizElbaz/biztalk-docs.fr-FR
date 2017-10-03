---
title: "Créer un Pack d’administration pour les personnalisations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ce1ffa0-57c7-41ce-b459-48c36522889e
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d04b29cd96a66057d83b5212472f0ea69150f0c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-a-new-management-pack-for-customizations"></a>Créer un Pack d’administration pour les personnalisations
La plupart des packs d’administration de fournisseur sont scellés afin que vous ne pouvez pas modifier les paramètres d’origine dans le fichier de pack d’administration. Toutefois, vous pouvez créer des personnalisations, tels que de nouveaux objets de remplacement ou d'analyse, et les enregistrer dans un pack d'administration différent. Par défaut, Operations Manager 2007 R2/2012 enregistre toutes les personnalisations dans le Pack d’administration par défaut. Comme meilleure pratique, vous devez plutôt créer un pack d’administration distinct pour chaque pack d’administration scellé que vous souhaitez personnaliser.  
  
 La création d'un pack d'administration pour le stockage des remplacements offre les avantages suivants :  
  
-   Il simplifie le processus d'exportation des personnalisations créées dans vos environnements de préproduction et de test vers votre environnement de production. Par exemple, plutôt que d’exporter le Pack d’administration par défaut qui contient des personnalisations à partir de plusieurs packs d’administration, vous pouvez exporter uniquement le pack d’administration qui contient les personnalisations d’un seul Pack d’administration.  
  
-   Vous pouvez supprimer le Pack d’administration d’origine sans devoir d’abord supprimer le Pack d’administration par défaut. Un Pack d’administration qui contient des personnalisations dépend du Pack d’administration d’origine. Cette dépendance nécessite que vous supprimiez le pack d'administration contenant les personnalisations avant de pouvoir supprimer le pack d'administration d'origine. Si toutes vos personnalisations sont enregistrées dans le Pack d’administration par défaut, vous devez supprimer le Pack d’administration par défaut avant de pouvoir supprimer un pack d’administration d’origine.  
  
-   Il est plus facile de suivre et de mettre à jour des personnalisations dans des packs d'administration individuels.  
  
 Pour plus d’informations sur les scellés et non scellés de packs d’administration, consultez [Management Pack Formats](http://go.microsoft.com/fwlink/?LinkID=198193) (http://go.microsoft.com/fwlink/?LinkId=198193). Pour plus d’informations sur les personnalisations des packs d’administration, consultez [personnalisation des packs d’administration](http://go.microsoft.com/fwlink/?LinkID=198194) (http://go.microsoft.com/fwlink/?LinkID=198194).