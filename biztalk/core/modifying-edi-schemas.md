---
title: "Modification des schémas EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6fa33c5e-17ca-4aaf-a1ca-1972a9bb45ac
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de196288f3f1d4475e6859e2440e4b03b1e521dc
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="modifying-edi-schemas"></a>Modification des schémas EDI
Vous pouvez modifier un schéma EDI existant, inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Une fois que vos partenaires commerciaux et vous avez convenu des modifications à apporter aux schémas standard et peut-être modifié le fichier MIG (Message Implementation Guideline) pertinent, vous pouvez modifier les schémas dans l'Éditeur BizTalk dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
> [!NOTE]
>  Certaines modifications de schéma (validation de champ croisé et fractionnement en sous-documents HIPAA) impliquent la modification des annotations d'un schéma EDI. Ces modifications ne peuvent pas être apportées dans l'Éditeur BizTalk, mais dans un éditeur de texte comme le Bloc-Notes.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="schema-naming-convention"></a>Convention d'affectation de noms de schémas  
 Un schéma EDI est identifié par son nom racine et son espace de noms. Vous ne pouvez pas déployer, dans le même groupe BizTalk, deux schémas ayant les mêmes nom racine et espace de noms. Vous ne pouvez pas modifier le nom racine d'un schéma EDI ou l'ajouter au nom racine car il doit contenir la version et le type de document dans une convention d'affectation de noms standard. Par conséquent, si vous voulez déployer, dans le même groupe BizTalk, deux schémas ayant le même nom racine, vous devez utiliser des espaces de noms différents.  
  
 Il n'est pas inhabituel pour une société de déployer, dans le même groupe BizTalk, une version différente du même schéma pour deux partenaires commerciaux ou plus. Dans ce cas, les deux schémas ont la même version et le même type de document. Pour déployer ces deux schémas, vous devez avoir des espaces de noms différents pour chaque schéma.  
  
## <a name="edi-schema-changes"></a>Modifications du schéma EDI  
 Vous pouvez apporter les modifications suivantes à un schéma EDI dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] :  
  
|Pour effectuer cette opération|Action|  
|----------------|-------------|  
|Modifier une énumération<br /><br /> (telle que la liste de valeurs dans une liste de codes)|Dans les propriétés d’un élément, ouvrez le **Éditeur d’énumération** et ajouter une valeur à ou supprimer une valeur de la liste d’énumération.|  
|Modifier le caractère facultatif d'un élément de données|Modifier la **Min Occurs** propriété. Changez-la en 0 pour rendre le champ facultatif ou en 1 pour le rendre obligatoire.|  
|Modifier le nombre maximal de fois qu'un élément de données peut apparaître dans le fichier|Modifier la **Max Occurs** propriété.|  
|Modifier le nombre de caractères dans l'élément de données|Modifier la **longueur** propriété.|  
|Modifier le type de données d'un élément de données|Modifier la **Base Data Type** ou **Type Date** propriété.|  
|Ajouter un champ personnalisé|Insérez un nœud de schéma Élément de champ enfant et définissez ses propriétés. **Remarque :** Ajout d’un attribut de champ enfant à un enregistrement dans un schéma EDI n’est pas autorisée, car la séquence des éléments ne serait pas garantie. La tentative d'ajout d'un attribut de champ enfant entraîne un schéma non valide. Vous pouvez uniquement ajouter un élément de champ enfant à un enregistrement dans un schéma EDI.|  
|Ajouter un enregistrement personnalisé|Insérez un nœud de schéma Enregistrement enfant, définissez ses propriétés, puis ajoutez les éléments de champ enfant.|  
|Supprimer un champ ou enregistrement personnalisé|Supprimez un champ ou enregistrement personnalisé avec ses éléments de champ enfant.|  
|Activer la validation de champ croisé|Définir l’indicateur de validation de champ croisé dans l’annotation dans la section appinfo du schéma à **Oui**. Cet indicateur est **X12ConditionDesignator_Check** (pour les schémas X12 ou HIPAA) ou **EdifactDependencyRule_Check** (pour les schémas EDIFACT).<br /><br /> Activez la validation de champ croisé pour un élément spécifique en spécifiant les conditions relationnelles (X12 et HIPAA) ou les règles de dépendance (EDIFACT). Pour plus d’informations, consultez [configuration de la Validation de champ croisé](../core/configuring-cross-field-validation.md).<br /><br /> Vous devez également définir le **validation de type Edi** propriété **Oui**.<br /><br /> La validation de champ croisé est activée par défaut pour les schémas HIPAA.|  
|Activer le fractionnement en sous-documents HIPAA|Dans un des schémas HIPAA que vous pouvez définir le fractionnement en sous-documents, définissez la **subdocument_break** et **Split_Without_Sibling_Data** propriétés du schéma à **Oui** et le **subdocument_creation_break** propriété pour un élément spécifique dans le schéma pour **Oui**.<br /><br /> Vous devez également définir le **entrants option de traitement par lots** propriété d’accord pour **fractionner l’échange en documents informatisés**.<br /><br /> Pour plus d’informations, consultez [fractionnement des sous-documents HIPAA](../core/splitting-hipaa-subdocuments.md).|  
|Ajouter des champs déclencheurs à un document HIPAA|Vous pouvez permettre au Désassembleur EDI de créer des enregistrements XML uniques pour un segment de votre document HIPAA, en fonction d'un élément de qualification nommé champ déclencheur. Vous devez spécifier les attributs décrivant le segment et la valeur de déclenchement qui provoque la création d'un enregistrement XML unique pour le segment. Pour plus d’informations, consultez [Annotations des champs déclencheurs HIPAA schéma](../core/hipaa-schema-trigger-field-annotations.md).|  
|Ajouter un segment à un document informatisé X12|Lorsque vous ajoutez un nouveau segment à un document informatisé X12, les trois premiers caractères du nom du segment servent d'identificateur de segment. Par conséquent, nous vous recommandons de nommer un segment en veillant à ce que les trois premiers caractères soient uniques.|  
|Ajouter une boucle à un document informatisé HIPAA|Lorsque vous ajoutez une nouvelle boucle à un document informatisé HIPAA, nous vous recommandons d'inclure « Loop » dans le nom de la boucle. Par exemple, le format d'une boucle est « TS837_2010AB_Loop ». **Remarque :** le premier segment dans une boucle est obligatoire (minOccurs du segment doit être égal à 1) afin d’éviter toute ambiguïté.|  
|Ajouter une boucle à sens quelconque à un document informatisé HIPAA|Lorsqu'un document informatisé a des segments équivalents avec des sémantiques différentes, vous devez les définir dans une SubLoop. Une SubLoop avec l’annotation XML \<xs : all\> permet des segments équivalents à se produire dans n’importe quel ordre.<br /><br /> Nous vous recommandons d'inclure « SubLoop » dans le nom de la boucle à sens quelconque. Un exemple de format est « TS837Q1_2010A_SubLoop » **Remarque :** les éléments d’une boucle à sens quelconque ne doivent se produire qu’une seule fois dans la boucle. Les frères d'une SubLoop doivent avoir un maxOccurs défini sur 1, afin d'éviter toute ambiguïté.|  
  
### <a name="to-modify-an-existing-edi-schema-in-biztalk-editor"></a>Pour modifier un schéma EDI existant dans l'Éditeur BizTalk  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ajoutez le schéma que vous voulez modifier à un projet et ouvrez le schéma dans l'Éditeur BizTalk.  
  
    > [!NOTE]
    >  Vous pouvez afficher le schéma dans un graphique en cliquant sur le **EDI** onglet en bas de l’écran de l’éditeur de schéma. Il est beaucoup plus facile d'accéder aux nœuds du schéma à l'aide de ce format tabulaire.  
  
2.  Pour modifier les propriétés d'un élément ou enregistrement de données, cliquez sur le nœud approprié sur le volet gauche de l'Éditeur BizTalk, puis modifiez ses propriétés dans la fenêtre Propriétés.  
  
3.  Pour modifier les valeurs d’une énumération, sélectionnez celle-ci dans le **propriétés** volet, puis cliquez sur les points de suspension pour ouvrir la **Éditeur d’énumération**. Ajouter ou supprimer dans la liste de valeurs, en veillant à ce qu’il existe une valeur sur chaque ligne dans le **valeurs** volet. Cliquez sur **OK**.  
  
4.  Pour ajouter un champ personnalisé au schéma, cliquez sur un nœud enregistrement dans l’arborescence de la console de l’Éditeur BizTalk, pointez sur **insérer un nœud de schéma**, puis cliquez sur **élément de champ enfant**. Nommez l'élément de données, puis faites glisser l'élément de données sur la position appropriée dans l'enregistrement. Définissez les propriétés de champ personnalisé comme requises.  
  
    > [!NOTE]
    >  L'ajout d'un attribut de champ enfant à un enregistrement dans un schéma EDI n'est pas autorisé car la séquence des éléments ne serait pas garantie. La tentative d'ajout d'un attribut de champ enfant entraîne un schéma non valide.  
  
5.  Pour ajouter un enregistrement personnalisé au schéma, cliquez sur un nœud enregistrement dans l’arborescence de la console de l’éditeur de schéma, pointez sur **insérer un nœud de schéma**, puis cliquez sur **enregistrement enfant**. Nommez l'enregistrement, puis faites glisser l'enregistrement sur la position appropriée dans le schéma. Ajoutez au moins un élément de données à l'enregistrement. Définissez les propriétés de l'enregistrement personnalisé comme requises.  
  
6.  Après avoir apporté les modifications souhaitées au schéma, vous pouvez modifier l’espace de noms cible qui s’applique à la propriété de schéma en cliquant sur le nœud racine (\<schéma\>), puis en remplaçant le **cible Namespace** propriété.  
  
7.  Enregistrez le schéma.  
  
8.  Valider le schéma en cliquant le schéma dans l’Explorateur de solutions et en cliquant sur **valider le schéma**.  
  
    > [!NOTE]
    >  Le **valider le schéma** commande validera le schéma EDI, car le **Extension de l’éditeur de schéma** propriété du nœud racine (\<schéma\>) est définie sur **EDI Extension de l’éditeur de schéma**.  
  
### <a name="to-modify-annotation-properties-in-an-existing-edi-schema"></a>Pour modifier les propriétés d'annotation dans un schéma EDI existant  
  
1.  Ouvrez le schéma dans un éditeur de texte, tel que le Bloc-Notes.  
  
2.  Pour activer la validation de champ croisé, procédez comme suit. Pour plus d’informations, consultez [configuration de la Validation de champ croisé](../core/configuring-cross-field-validation.md).  
  
    1.  Dans l’annotation appinfo en haut du schéma, définissez l’indicateur de validation de champ croisé (soit **X12ConditionDesignator_Check** pour les schémas X12 ou HIPAA ou **EdifactDependencyRule_Check** pour EDIFACT schémas) pour **Oui**.  
  
        > [!NOTE]
        >  L’indicateur de validation de champ croisé est **Oui** par défaut pour les schémas HIPAA de BizTalk Server.  
  
    2.  Dans l'annotation pour un élément spécifique, spécifiez les conditions relationnelles (X12 ou HIPAA) ou les règles de dépendance (EDIFACT) pour l'élément. Pour plus d’informations sur ces paramètres, consultez [Validation croisée du Segment de champ](../core/cross-field-segment-validation.md).  
  
        > [!NOTE]
        >  Dans le **Validation** page (sous la **paramètres des documents informatisés** section) de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue pour l’accord approprié, Assurez-vous que le **Validation de type EDI** propriété est sélectionnée.  
  
3.  Pour activer le fractionnement en sous-documents HIPAA, procédez comme suit. Pour plus d’informations, consultez [fractionnement des sous-documents HIPAA](../core/splitting-hipaa-subdocuments.md).  
  
    1.  Dans l’annotation appinfo en haut du schéma, définissez la **subdocument_break** et **Split_Without_Sibling_Data** indicateurs à **Oui**.  
  
    2.  Dans l’annotation appinfo pour un élément spécifique, consultez la **subdocument_creation_break** indicateur **Oui**.  
  
        > [!NOTE]
        >  Dans le **paramètres d’hôte Local** page (sous la **paramètres de l’échange** section) de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue pour le accord, assurez-vous que le **entrants option de traitement par lots** est définie sur **fractionner l’échange en documents informatisés**.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement des schémas EDI](../core/developing-edi-schemas.md)