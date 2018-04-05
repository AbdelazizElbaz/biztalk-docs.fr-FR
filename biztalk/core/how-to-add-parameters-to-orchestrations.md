---
title: Comment ajouter des paramètres aux Orchestrations | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, parameters
ms.assetid: 35c731ed-6327-4de7-8d2e-4d14024bda77
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8328a97631efb2b8454e0a2679b257d35402cf4c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-parameters-to-orchestrations"></a>Ajout de paramètres aux orchestrations
Vous pouvez spécifier les paramètres de votre orchestration dans la fenêtre Vue Orchestration. Une orchestration accepte les éléments suivants comme paramètres :  
  
-   Messages  
  
-   Variables (objets inclus)  
  
-   Ensembles de corrélations  
  
-   Liens de rôle  
  
-   Ports  
  
 Les paramètres peuvent être transmis entre les orchestrations en tant que paramètres d'entrée ou de sortie. Les premiers peuvent être transmis par valeur ou référence, et les seconds uniquement par référence. Les paramètres incluent les variables, messages, ensembles de corrélations, liens de rôle et ports.  
  
### <a name="to-set-orchestration-parameters"></a>Pour définir des paramètres d'orchestration  
  
1.  Dans la fenêtre Vue Orchestration, utilisez le **paramètres de l’Orchestration** dossier pour ajouter des ports, des messages et des variables.  
  
2.  Pour chaque élément ajouté à la **paramètres de l’Orchestration** dossier, utilisez la fenêtre Propriétés pour spécifier la **Direction** propriété :  
  
    -   Avant : paramètre transmis par valeur.  
  
    -   Réf. : paramètre transmis par référence.  
  
    -   Arrière : paramètre transmis par référence.  
  
### <a name="to-add-a-parameter-to-an-orchestration"></a>Pour ajouter un paramètre à une orchestration  
  
1.  Dans la fenêtre Vue Orchestration, cliquez sur le **paramètres de l’Orchestration** dossier puis cliquez sur le type de paramètre.  
  
2.  Pour les liens de rôle et les ports configurés, servez-vous de l'Assistant pour configurer le paramètre.  
  
     — Ou :  
  
     Pour tout autre type de paramètre, effectuez la configuration dans la page des propriétés.  
  
 **Types de paramètres**  
  
 Les paramètres peuvent être passés par valeur, en tant que paramètres de référence ou paramètres de sortie. Lorsqu'un paramètre est passé par valeur à une orchestration, une copie des données est effectuée et utilisée par l'orchestration.  
  
 Lorsque vous utilisez un paramètre de référence, aucune copie n'est réalisée. L'emplacement de mémoire contenant les données est partagé entre le programme appelant et l'orchestration, et son contenu peut être modifié par l'orchestration. Une telle modification implique la modification de la valeur du paramètre dans l'orchestration mais aussi dans le programme appelant.  
  
 Un paramètre de sortie est similaire au paramètre de référence, mais l'orchestration ne peut pas supposer qu'il contient des données valides lors de sa transmission. Le programme appelant attend de l'orchestration qu'elle affecte une valeur au paramètre.  
  
 **Règles pour les paramètres de l’orchestration**  
  
-   Vous ne pouvez transmettre les messages et les variables (objets inclus) qu'en tant que paramètres de référence ou de sortie.  
  
-   Impossible de transmettre ou de référencer des paramètres à une orchestration dans un **démarrer Orchestration** forme.  
  
-   Les paramètres d'entrée, incluant les liens de rôle et les ports dynamiques, doivent se voir attribuer une valeur avant d'être transmis à une orchestration.  
  
## <a name="see-also"></a>Voir aussi  
 [Formes d’orchestration](../core/orchestration-shapes.md)   
 [Comment ajouter des formes aux Orchestrations](../core/how-to-add-shapes-to-orchestrations.md)   
 [Comment utiliser le Type de boîte de dialogue Sélectionnez artefact](../core/how-to-use-the-select-artifact-type-dialog-box.md)