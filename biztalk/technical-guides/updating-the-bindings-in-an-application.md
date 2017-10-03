---
title: "Mise à jour les liaisons dans une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe4ee4d8-67bf-4137-94e2-8274107c8ed6
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d4d30296a2bb81b3685793884010f02eb950828
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="updating-the-bindings-in-an-application"></a>Mise à jour les liaisons de l’Application
Lorsque vous mettez à jour un assembly dans une application, ses liaisons sont généralement remplacées, faute de quoi l'assembly risque de ne pas être lié, vous obligeant à une reconfiguration manuelle des liaisons. Pour éviter ce problème, vous pouvez utiliser un fichier de liaison à mettre à jour de la même version de l’assembly ou de mettre à jour un assembly avec une version plus récente.  
  
## <a name="updating-the-same-version-of-an-assembly"></a>Mise à jour de la même Version d’un Assembly  
 si l'assembly possède des ports dynamiques ou des ports à liaison anticipée et que vous ayez modifié leur configuration dans la console Administration de BizTalk Server, vous perdez ces paramètres lors de la mise à jour de l'assembly avec un assembly de même version. Vous pouvez exporter un fichier de liaison pour l’assembly que vous vous apprêtez à mettre à jour. Après la mise à jour de l’assembly, vous pouvez importer l’assembly dans l’application et puis importer son fichier de liaison pour réappliquer les liaisons précédentes.  
  
## <a name="updating-an-assembly-with-a-newer-version"></a>Mise à jour d’un Assembly avec une Version plus récente  
 Vous pouvez mettre à jour la version d’un assembly en exportant la liaison associée à un assembly unique dans un fichier de liaison, modification du fichier de liaison afin de refléter une nouvelle version de l’assembly, puis importer les liaisons de l’assembly dans l’application. Pour plus d’informations sur la modification d’un fichier de liaison, consultez [personnalisation des fichiers de liaison](http://go.microsoft.com/fwlink/?LinkID=155000) (lien hypertexte « http://go.microsoft.com/fwlink/?LinkID=155000 » http://go.microsoft.com/fwlink/?LinkID=155000) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.