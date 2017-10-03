---
title: "L’importation de schémas JD Edwards OneWorld dans des projets BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generating schemas
- importing schemas
- schemas, generating
- schemas, importing into BizTalk Server projects
ms.assetid: 5bcaa276-8c76-4212-b373-de86e3008a69
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35b0d7fec5acc991ae6c141f57297b7511281be3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="importing-jd-edwards-oneworld-schemas-into-biztalk-server-projects"></a>Importation de schémas JD Edwards OneWorld dans des projets BizTalk Server
Cette rubrique traite de la recherche d'un serveur JD Edwards OneWorld et de l'importation des schémas dans un projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
> [!NOTE]
>  Vous devez vérifier que vous avez défini le fichier arglist. Vous devez également mettre à jour le fichier jdearglist.txt avant de générer les schémas dans l'orchestration. Pour plus d’informations, consultez [gestion des valeurs de chaîne](../core/handling-string-values1.md).  
  
> [!NOTE]
>  Chaque fois que vous modifiez le fichier jdearglist, vous devez régénérer les schémas pour cet objet métier.  
  
 Après avoir créé le système logique JD Edwards OneWorld, vous pouvez parcourir JD Edwards OneWorld en ouvrant l'Assistant Adaptateur Microsoft à partir d'un projet BizTalk Server.  
  
### <a name="to-import-schemas"></a>Pour importer des schémas  
  
1.  Ouvrez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
2.  Avec le bouton droit le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de projet, pointez sur **ajouter**, puis sélectionnez **ajouter les éléments générés**.  
  
3.  Cliquez sur **ajouter un adaptateur**, puis sélectionnez **ouvrir**.  
  
4.  Sélectionnez la carte, puis cliquez sur **suivant**.  
  
     Le JD. Système d’Edwards OneWorld XE s’affiche dans le navigateur.  
  
     ![](../core/media/jdedadapter-04-jdebrowse.gif "JDEdAdapter_04_JDEBrowse")  
  
     L'assistant Adaptateur affiche une arborescence de tous les systèmes définis. JD Edwards OneWorld possède un nombre de modules trop important pour tous les afficher dans un seule grande liste. Les modules sont regroupés selon les trois premiers caractères de leur nom.  
  
    -   Le premier niveau de la hiérarchie correspond à la liste des préfixes à trois caractères des noms de module.  
  
    -   Le second niveau inclut les modules qui partagent le même préfixe à trois caractères.  
  
    -   Le dernier niveau répertorie les fonctions commerciales appartenant à un module. Lorsque vous développez l'icône des services, vous affichez ses opérations.  
  
     Le développement d'une opération affiche les arguments d'entrée/de sortie.  
  
     Vous pouvez développer les arguments d'entrée/de sortie pour afficher les types de données des arguments.  
  
    > [!NOTE]
    >  Si les définitions d'objet serveur sont modifiées, vous devez régénérer le schéma afin d'actualiser les données qu'il contient.  
  
    > [!NOTE]
    >  Si vous modifiez le fichier jdearglist.txt après avoir généré votre schéma, vous devez régénérer le schéma pour actualiser les données qu'il contient. Pour plus d’informations sur le fichier jdearglist.txt, consultez [gestion des valeurs de chaîne](../core/handling-string-values1.md).  
  
## <a name="generating-schemas"></a>Création de schémas  
 La procédure suivante permet de générer des schémas.  
  
#### <a name="to-generate-schemas"></a>Pour créer des schémas  
  
1.  Sélectionnez l'élément pour lequel vous souhaitez importer des schémas.  
  
2.  Cliquez sur (ou faites glisser) pour ajouter l’élément à la **transmission** volet (pour un trafic entrant vers JD Edwards OneWorld call).  
  
3.  Cliquez sur **OK**.  
  
     Les schémas générés pour l'élément JD Edwards OneWorld sélectionné sont importés dans le projet BizTalk Server.  
  
> [!NOTE]
>  Lors de l’utilisation de carnet d’adresses (N0100041) le nom du champ est **cActionCode**. L'action fait partie du fichier XML lui-même. Les codes suivants sont utilisés :  
>   
>  --A pour Ajouter ;  
>   
>  --C pour Modifier ;  
>   
>  --D pour Supprimer ;  
>   
>  --I pour Requête.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de gestionnaires de JD Edwards OneWorld envoi](../core/creating-jd-edwards-oneworld-send-handlers.md)