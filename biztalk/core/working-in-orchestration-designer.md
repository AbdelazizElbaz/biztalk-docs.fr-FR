---
title: "Dans le Concepteur d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, saving
- deleting, orchestrations
- projects, orchestrations
- orchestrations, properties
- orchestrations, creating
- creating, orchestrations
- naming conventions, orchestrations
- orchestrations, naming conventions
- orchestrations, deleting
ms.assetid: 13e72b41-d9b6-4508-9a44-b3c7c1804f36
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52eb574f9f6b55b784357ff03c05ccb23774fecb
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="working-in-orchestration-designer"></a>Utilisation du Concepteur d'orchestration
Après avoir ouvert un projet BizTalk, vous pouvez créer de nouvelles orchestrations et ajouter des orchestrations existantes au projet. Les procédures suivantes vous expliquent comment créer et enregistrer une orchestration, ajouter une orchestration existante à un projet ou en supprimer une, modifier le nom d'une orchestration et définir les propriétés d'une orchestration.  
  
### <a name="to-create-an-orchestration"></a>Pour créer une orchestration  
  
1.  Dans l’Explorateur de solutions, cliquez sur le nom du projet, sélectionnez **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue le **catégories** volet, cliquez sur **des éléments de projet BizTalk**, puis, dans le **modèles** volet, cliquez sur **Orchestration BizTalk**.  
  
3.  Dans le **nom** zone située au bas de la boîte de dialogue, fournissez un nom pour l’orchestration, puis cliquez sur **ajouter**.  
  
     La nouvelle orchestration est créée et s'affiche dans le Concepteur d'orchestration, et un fichier .odx correspondant est créé et affiché dans l'Explorateur de solutions.  
  
### <a name="to-add-an-existing-orchestration-to-a-project"></a>Pour ajouter une orchestration existante à un projet  
  
1.  Dans l’Explorateur de solutions, cliquez sur le nom du projet, cliquez sur **ajouter**, puis cliquez sur **élément existant**.  
  
2.  Dans le **ajouter un élément existant** boîte de dialogue, accédez au répertoire contenant l’orchestration, sélectionnez l’orchestration, puis cliquez sur **ajouter**.  
  
     L'orchestration est ajoutée au projet.  
  
    > [!NOTE]
    >  Lorsque vous ajoutez un fichier existant, le fichier est copié vers votre projet (il n'est pas simplement ajouté par référence). Si vous modifiez le fichier dans votre projet, le fichier original reste en l'état.  
  
### <a name="to-change-the-name-of-an-orchestration"></a>Pour modifier le nom d'une orchestration  
  
1.  Dans l’Explorateur de solutions, cliquez sur le fichier .odx que vous souhaitez modifier, puis cliquez sur **renommer**.  
  
2.  Tapez le nouveau nom de fichier de votre choix, puis appuyez sur ENTRÉE.  
  
    > [!NOTE]
    >  Lorsque vous modifiez le nom d’un fichier .odx, vous pouvez également modifier le nom du type d’orchestration en cliquant sur l’aire de conception pour afficher la fenêtre Propriétés et modifiez la valeur de la **Typename** propriété de la orchestration.  
  
### <a name="to-save-an-orchestration"></a>Pour enregistrer une orchestration  
  
-   Sur le **fichier** menu, cliquez sur **enregistrer \<nom de l’orchestration\>**.  
  
    > [!NOTE]
    >  Fichiers d’orchestration sont enregistrées au format UTF-8.  Schémas, mappages et pipelines sont enregistrés au format UTF-16.  
  
### <a name="to-remove-an-orchestration-from-a-project"></a>Pour supprimer une orchestration d'un projet  
  
-   Dans l’Explorateur de solutions, cliquez sur le fichier que vous souhaitez supprimer, puis cliquez sur **exclure du projet**.  
  
    > [!NOTE]
    >  Pour supprimer l’orchestration d’un projet et supprimer définitivement le fichier, cliquez sur **supprimer** à la place.  
  
### <a name="to-include-an-excluded-orchestration-in-a-project"></a>Pour inclure une orchestration exclue dans un projet  
  
-   Dans l’Explorateur de solutions, cliquez sur le **afficher tout** bouton de barre d’outils, le fichier .odx de clic droit et sélectionnez **inclure dans le projet**.  
  
### <a name="to-set-orchestration-properties"></a>Pour définir les propriétés de l'orchestration  
  
1.  Ouvrez l'orchestration en double-cliquant sur le fichier.odx du projet, ou en sélectionnant l'onglet contenant l'orchestration dans la zone de processus.  
  
2.  Dans la fenêtre Vue Orchestration, sélectionnez **propriétés d’Orchestration**.  
  
     — Ou :  
  
     Cliquez sur le **zone de processus** en arrière-plan de l’aire de conception d’Orchestration.  
  
3.  Dans la fenêtre Propriétés, définissez les propriétés suivantes. Notez que certaines propriétés n'apparaissent que dans certaines circonstances.  
  
    > [!NOTE]
    >  Les noms des orchestrations, des types de ports et des types de messages à parties multiples doivent être uniques dans toute l'étendue d'un module.  
  
    |Propriété| Description|  
    |--------------|-----------------|  
    |Traitement|Détermine si une orchestration de transaction atomique peut être mise en lot avec d'autres instances.|  
    |Compensation|Indique le type de compensation à effectuer dans l'orchestration.|  
    |Niveau d'isolement|Pour les orchestrations transactionnelles, détermine le niveau auquel les données sont accessibles parmi les transactions simultanées.|  
    |Module Exportable|Détermine si le module peut être exporté ou non vers BPEL4WS.|  
    |Espace de noms cible XML du module|Espace de noms cible XML utilisé pour l'exportation des types vers BPEL4WS.|  
    |Espace de noms|Détermine le nom du module contenant qui inclut l'orchestration et les types d'orchestrations.|  
    |Orchestration exportable|Indique si cette orchestration est censée être exportable ou non vers BPEL4WS.|  
    |Espace de noms cible de l'orchestration XML|Espace de noms cible XML utilisé pour l'exportation de cette orchestration vers BPEL4WS.|  
    |Réessayer|Indique s'il faut retenter une orchestration transactionnelle en cas d'échec.|  
    |Délai d'expiration|Délai en secondes après lequel une orchestration transactionnelle est considérée comme ayant échoué pour cause d'inactivité.|  
    |Identificateur de la transaction|Identificateur unique d'une orchestration transactionnelle.|  
    |Type de transaction|Indique si l'orchestration est une transaction atomique, une transaction longue ou si elle n'est pas traitée.|  
    |Modificateur de type|Détermine l'étendue des variables au niveau de l'orchestration.<br /><br /> Privé : l'accès à cette orchestration est limité au module contenant.<br /><br /> Public : l'accès à cette orchestration n'est pas limité.<br /><br /> Interne : l'accès à cette orchestration est limité aux modules d'un même projet.|  
    |Nom du type|Détermine le nom de cette orchestration dans le module contenant. **Remarque :** si vous permet d’utiliser un nom de type qui est identique à un espace de noms racine, vous pouvez recevoir une erreur à partir du Concepteur d’Orchestration lorsque vous définissez des messages et affecter des variables basées sur le Typename et tentez d’effectuer des opérations sur les. Par exemple, si vous choisissez le nom de type System, puis définissez des messages et des variables en tant que System.String, une erreur risque de se produire.|  
  
## <a name="see-also"></a>Voir aussi  
 [Formes d’orchestration](../core/orchestration-shapes.md)   
 [Comment ajouter des formes aux Orchestrations](../core/how-to-add-shapes-to-orchestrations.md)   
 [Comment ajouter des paramètres aux Orchestrations](../core/how-to-add-parameters-to-orchestrations.md)   
 [Comment utiliser le Type de boîte de dialogue Sélectionnez artefact](../core/how-to-use-the-select-artifact-type-dialog-box.md)