---
title: "Mise à jour d’une Configuration existante avec un fichier de liaison | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding files, updating
- binding files, rules
- artifacts, binding files
- binding files, unbinding
- binding files, customizing
- artifacts, updating
ms.assetid: 11580e59-7147-42d0-a976-f6b5e6933d24
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03b17ee54f053fb6a81b3855ffbcbcc1e776f513
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="updating-an-existing-configuration-with-a-binding-file"></a>Mise à jour d'une configuration existante à l'aide d'un fichier de liaison
Les informations contenues dans un fichier de liaison annulent et remplacement celles de la configuration existante. Si le nom d'un artefact dans un fichier de liaison correspond au nom d'un artefact dans votre configuration existante, l'artefact du fichier de liaison met à jour l'artefact de votre configuration existante lorsque vous importez le fichier de liaison.  
  
 Certaines règles sont suivies lors de la mise à jour d'artefacts existants à l'aide des artefacts d'un fichier de liaison. Cette rubrique est consacrée aux règles suivies lors de la mise à jour d'artefacts dans une configuration existante à l'aide des artefacts d'un fichier de liaison.  
  
 Dans cette section, on suppose que le fichier de liaison contient des valeurs valides lors de son importation et aucun scénario mettant en scène un fichier de liaison contenant des valeurs invalides ne sera envisagé.  
  
## <a name="rules-followed-by-biztalk-server-when-updating-a-configuration-with-a-binding-file"></a>Règles suivies par BizTalk Server lors de la mise à jour d'une configuration à l'aide d'un fichier de liaison  
 BizTalk Server suit certaines règles lors de la mise à jour d'artefacts existants à l'aide d'artefacts correspondants dans un fichier de liaison. En général, les règles suivantes sont applicables :  
  
-   Les zones de texte et les cases à cocher exposées lors de la configuration d'un artefact par l'intermédiaire de l'interface utilisateur de BizTalk Server (à l'aide de la console Administration de BizTalk Server ou de l'Explorateur BizTalk, par exemple), doivent être définies sur une valeur spécifique ou être laissées vides. Les valeurs fournies pour les artefacts d'un fichier de liaison définissent la valeur de l'interface utilisateur pour les éléments mis à jour.  
  
-   Les zones déroulantes exposées lors de la configuration d'un artefact par l'intermédiaire de l'interface utilisateur de BizTalk Server doivent être définies sur une valeur spécifique ou sur "Aucune". Les valeurs fournies pour les artefacts d'un fichier de liaison définissent la valeur de l'interface utilisateur pour les éléments mis à jour.  
  
-   Les vues de la grille de données exposées lors de la configuration d'un artefact par l'intermédiaire de l'interface utilisateur de BizTalk Server sont mises à jour avec les listes d'éléments correspondants dans le fichier de liaison. La liste associée à la vue de la grille de données est toujours remplacée par la liste du fichier de liaison, sauf si la liste de la vue de la grille de données est liée à un port ou à un emplacement de réception. Dans ce cas, la liste du fichier de liaison fusionne avec la liste de la vue de la grille de données existante.  
  
-   Les artefacts du fichier de liaison sont identifiés par une valeur de clé primaire. La valeur associée à la clé primaire d'un artefact ne peut jamais être définie sur Null dans l'interface utilisateur ; tous les artefacts du fichier de liaison doivent donc avoir une valeur de clé primaire. Si la valeur associée à la clé primaire d'un artefact du fichier de liaison correspond à la valeur associée à la clé primaire d'un artefact dans une configuration existante, ces artefacts sont considérés comme identiques ou correspondants. Si l'artefact du fichier de liaison et l'artefact existant sont identiques, l'artefact existant est mis à jour à l'aide de l'artefact du fichier de liaison, comme l'explique le tableau ci-dessous. Si un artefact du fichier de liaison contient une valeur de clé primaire unique, alors un nouvel artefact est créé dans la configuration de BizTalk Server lors de l'importation du fichier de liaison.  
  
 Le tableau suivant décrit le comportement attendu lors de la mise à jour des artefacts d'une configuration existante à l'aide d'artefacts correspondants, suite à l'importation d'un fichier de liaison.  
  
|Type d'artefact|Propriété|Occurrences possibles pour la propriété spécifiée.|Champ de l'interface utilisateur|Impact de l'importation d'un artefact existant depuis un fichier de liaison.|  
|-------------------|--------------|------------------------------------------------|--------------------------|--------------------------------------------------------------|  
|**Tiers**|Nom|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone de texte|Clé primaire|  
||Alias|Min Occurs : 0<br /><br /> Max Occurs : *|Grille de données|Remplacer la liste d'alias par la liste d'alias du fichier de liaison.|  
||Ports d'envoi|Min Occurs : 0<br /><br /> Max Occurs : *|Grille de données|Fusionner la liste de ports existante pour ce tiers avec la liste de ports pour ce tiers dans le fichier de liaison.|  
||Nom commun du certificat et empreinte|Min Occurs : 0<br /><br /> Max Occurs : 1<br /><br /> (par propriété)|Zone de texte|Remplacer ces valeurs par celles du fichier de liaison. Si ces valeurs n'existent pas dans le fichier de liaison, elles sont alors définies sur Null.|  
|**Orchestration**| Description|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone de texte|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison.|  
||Hôte|Min Occurs : 0<br /><br /> Max Occurs : 1|Zone déroulante|Remplacer cette valeur par celle du fichier de liaison. Si cette valeur n'existe pas dans le fichier de liaison, elle est alors définie sur Null.|  
||Ports d'entrée et ports de sortie|Min Occurs : 0<br /><br /> Max Occurs : *|Zone déroulante|Lier un port logique à un port physique existant. Le port physique peut exister dans les emplacements suivants :<br /><br /> -Dans le groupe.<br />-Dans l’application.<br />-Dans le fichier de liaison.<br /><br /> Vous pouvez également définir le port sur **aucun**. Si la valeur **aucun** le port logique n’est pas lié à n’importe quelle ressource.|  
||Cases à cocher des propriétés de suivi|Min Occurs : 1<br /><br /> Max Occurs : 1<br /><br /> (par propriété)|Case à cocher|Remplacer ces valeurs avec les valeurs spécifiées dans le fichier de liaison.|  
|**Groupe de ports d’envoi**|Nom|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone de texte|Clé primaire|  
||Ports d’envoi|Min Occurs : 0<br /><br /> Max Occurs : *|Grille de données|Fusionner la liste de ports existante pour ce groupe de ports d'envoi avec le groupe de ports d'envoi spécifié dans le fichier de liaison.|  
||Filtres|Min Occurs : 0<br /><br /> Max Occurs : *|Grille de données|Remplacer la liste de filtres pour ce groupe de ports d’envoi existante avec la liste de filtres pour ce groupe de ports d’envoi spécifié dans le fichier de liaison.|  
|**Port d’envoi**|Nom|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone de texte|Clé primaire|  
||Transport - Type|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone déroulante|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison.|  
||Transport - Gestionnaire d'envoi|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone déroulante|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison.|  
||Pipeline d’envoi|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone déroulante|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison.|  
||Nombre de tentatives, Intervalle avant nouvelle tentative et Priorité|Min Occurs : 1<br /><br /> Max Occurs : 1<br /><br /> (par propriété)|Zone de défilement|Remplacer ces valeurs avec les valeurs spécifiées dans le fichier de liaison.|  
||Livraison chronologique des messages|Min Occurs : 1<br /><br /> Max Occurs : 1|Case à cocher|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison.|  
||Activer le routage des messages ayant échoué|Min Occurs : 1<br /><br /> Max Occurs : 1|Case à cocher|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison.|  
||Activer la fenêtre de service|Min Occurs : 1<br /><br /> Max Occurs : 1|Case à cocher|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison.|  
||Heure de début de la fenêtre de service et heure de fin de la fenêtre de service|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone de défilement|Remplacer ces valeurs avec les valeurs spécifiées dans le fichier de liaison.|  
||Cartes|Min Occurs : 0<br /><br /> Max Occurs : *|Grille de données|Remplacer la liste de mappages existante pour ce groupe de ports d'envoi par la liste de mappages pour ce groupe de ports d'envoi spécifiée dans le fichier de liaison.|  
||Filtrer|Min Occurs : 0<br /><br /> Max Occurs : *|Grille de données|Remplacer la liste de filtres existante pour ce groupe de ports d'envoi par la liste de filtres pour ce groupe de ports d'envoi spécifiée dans le fichier de liaison.|  
||Nom commun du certificat|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone de texte|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison.|  
||Empreinte de certificat|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone de texte|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison.|  
||Suivi|Min Occurs : 0<br /><br /> Max Occurs : 1|Case à cocher|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison.|  
||Type de transport secondaire|Min Occurs : 0<br /><br /> Max Occurs : 1|Zone déroulante|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison.|  
||Transports secondaires URI|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone de texte|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison. Valide uniquement si le type de transport secondaire est défini.|  
||Gestionnaire d'envoi de transport secondaire|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone déroulante|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison. Valide uniquement si le type de transport secondaire est défini.|  
||Nombre de tentatives de transport secondaire|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone de défilement|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison. Valide uniquement si le type de transport secondaire est défini.|  
||Intervalle avant nouvelle tentative de transport secondaire|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone de défilement|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison. Valide uniquement si le type de transport secondaire est défini.|  
||Activer la fenêtre de service pour le transport secondaire|Min Occurs : 1<br /><br /> Max Occurs : 1|Case à cocher|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison. Valide uniquement si le type de transport secondaire est défini.|  
||Heure de début de la fenêtre de service et heure de fin de la fenêtre de service pour le transport secondaire|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone de défilement|Remplacer ces valeurs avec les valeurs spécifiées dans le fichier de liaison. Valide uniquement si le type de transport secondaire est défini et si la valeur Activer la fenêtre de service est définie.|  
|**Port de réception**|Nom|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone de texte|Clé primaire|  
||Paramètres d'authentification (boutons radio)|Min Occurs : 1<br /><br /> Max Occurs : 1|Bouton radio|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison.|  
||Activer le routage pour les messages ayant échoué|Min Occurs : 1<br /><br /> Max Occurs : 1|Case à cocher|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison.|  
|| Description|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone de texte|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison.|  
||Emplacements de réception|Min Occurs : 0<br /><br /> Max Occurs : *|Grille de données|Remplacer la liste d'emplacements de réception existante pour ce port de réception par la liste d'emplacements de réception pour ce port de réception spécifiée dans le fichier de liaison. Si tous les emplacements de réception du fichier de liaison existent déjà dans le groupe, l'importation échoue.|  
||Cartes|Min Occurs : 0<br /><br /> Max Occurs : *|Grille de données|Remplacer la liste de mappages existante pour ce port de réception par la liste de mappages pour ce port de réception spécifiée dans le fichier de liaison.|  
||Suivi - Propriétés de suivi des corps de message et des messages|Min Occurs : 1<br /><br /> Max Occurs : 1<br /><br /> (par case à cocher)|Case à cocher|Remplacer ces valeurs avec les valeurs spécifiées dans le fichier de liaison.|  
|**Emplacement de réception**|Nom|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone de texte|Clé primaire|  
||Type de transport |Min Occurs : 1<br /><br /> Max Occurs : 1|Zone déroulante|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison.|  
||Gestionnaire de réception|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone déroulante|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison.|  
||Pipeline|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone déroulante|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison.|  
|| Description|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone de texte|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison.|  
||Cases à cocher et zones déroulantes Date de début et date de fin de la planification.|Min Occurs : 1<br /><br /> Max Occurs : 1|Case à cocher et zone déroulante.|Remplacer ces valeurs avec les valeurs spécifiées dans le fichier de liaison. Les valeurs des dates sont importées même si les valeurs de la case à cocher ne sont pas activées.|  
||Case à cocher Activer la fenêtre de service|Min Occurs : 1<br /><br /> Max Occurs : 1|Case à cocher|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison.|  
||Heure de début de la fenêtre de service et heure de fin de la fenêtre de service|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone de défilement|Remplacer ces valeurs avec les valeurs spécifiées dans le fichier de liaison. Valide uniquement si la valeur Activer la fenêtre de service est définie.|  
|**Schéma**| Description|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone de texte|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison.|  
||Suivi - Toujours suivre toutes les propriétés|Min Occurs : 1<br /><br /> Max Occurs : 1|Case à cocher|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison.|  
||Suivi - Sélectionner toutes les propriétés de message|Min Occurs : 1<br /><br /> Max Occurs : 1|Case à cocher|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison. Si cette valeur est activée, alors toutes les propriétés de message pouvant être cochées sont également activées.|  
||Suivi - propriétés individuelles|Min Occurs : 0<br /><br /> Max Occurs : *|Cases à cocher|Remplacer la liste de propriétés suivies existante pour ce schéma par la liste de propriétés suivies pour ce schéma spécifiée dans le fichier de liaison.<br /><br /> Si un fichier de liaison importé fait référence à des propriétés suivies qui ne sont pas disponibles pour le schéma existant, une erreur est générée.|  
|**Carte**| Description|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone de texte|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison.|  
|**Pipeline**| Description|Min Occurs : 1<br /><br /> Max Occurs : 1|Zone de texte|Remplacer cette valeur avec la valeur spécifiée dans le fichier de liaison.|  
||Événements de suivi|Min Occurs : 1<br /><br /> Max Occurs : 1<br /><br /> (par case à cocher)|Case à cocher|Remplacer ces valeurs avec les valeurs spécifiées dans le fichier de liaison.|  
||Suivre les corps des messages|Min Occurs : 1<br /><br /> Max Occurs : 1<br /><br /> (par case à cocher)|Case à cocher|Remplacer ces valeurs avec les valeurs spécifiées dans le fichier de liaison.|  
|**Stratégie**|Non applicable. Les stratégies ne sont pas exportables dans un fichier de liaison.|Non applicable|Non applicable|Non applicable|  
|**Lien de rôle**|Non applicable. Les liens de rôle ne sont pas exportables dans un fichier de liaison.|Non applicable|Non applicable|Non applicable|  
  
## <a name="unbinding-behavior-when-updating-existing-artifacts-with-matching-artifacts-in-a-binding-file"></a>Comportement d'annulation de liaison lors de la mise à jour d'artefacts existants à l'aide d'artefacts correspondants dans un fichier de liaison  
 Les artefacts d'un fichier de liaison sont configurés par défaut pour faire référence à d'autres artefacts ; par exemple, un port de réception est généralement configuré pour faire référence à un emplacement de réception. Dans ce scénario, le port de réception est l'artefact parent et l'emplacement de réception est l'artefact enfant. Le port de réception est **explicitement** configuré pour faire référence à l’emplacement de réception et l’emplacement de réception puis **implicitement** fait référence au port de réception. S'il existe des artefacts parents dont la configuration est incomplète dans un fichier de liaison (si par exemple un port de réception n'est pas configuré avec un emplacement de réception), ceux-ci ne seront pas complètement configurés après l'importation du fichier de liaison, quel que soit leur état dans la configuration existante. Par exemple, si vous disposez d’un de réception myrp de port est configuré sans emplacement de réception myRL et le port de réception myrp identique dans le fichier de liaison est **pas** configuré avec emplacement de réception myRL, puis l’entrée du fichier de liaison priorité. Pour cette activité de réception exemple myRP de port ne sera pas configuré avec un emplacement de réception après avoir importé le fichier de liaison, donc vous aurez efficacement **indépendant** myRL de myRP.  
  
 Cette règle ne s'applique qu'à l'importation d'artefacts contenant des références explicites et non à l'importation d'artefacts contenant des références implicites. Donc, si vous avez importé un mappage qui contient des références implicites à (ou est explicitement référencé par) 10 autres artefacts, vous ne devez pas vous inquiéter de l'annulation de la liaison entre le mappage et les artefacts auxquels il est fait implicitement référence.  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation des fichiers de liaison](../core/customizing-binding-files.md)