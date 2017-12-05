---
title: "Problèmes connus avec les outils XML utilisés avec les Solutions EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03d9b361-be98-494c-b32d-03892672fef1
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23b8222369503f616f2d994f9292091f8e6c1f0d
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="known-issues-with-xml-tools-used-with-edi-solutions"></a>Problèmes connus avec les outils XML utilisés avec les solutions EDI
Cette rubrique décrit les problèmes connus avec les outils XML dans BizTalk Server.  
  
## <a name="validation-of-test-map-input-and-output-file-still-occurs-when-the-validate-property-is-set-to-false"></a>Les fichiers d'entrée et de sortie TestMap sont validés même si la propriété Valider est définie sur False  
 Si vous testez un mappage avec la propriété entrée TestMap **natif** et les propriétés valider l’entrée TestMap et valider la sortie TestMap **False**, la validation est toujours effectuée. Cela est dû au fait que le fichier d'entrée natif est converti au format XML et que BizTalk Server valide le code XML par rapport au schéma. S’il existe des problèmes de validation dans le fichier d’entrée, ce mécanisme de validation génère des erreurs, même si les propriétés valider l’entrée TestMap et valider la sortie TestMap sont définies sur **False**.  
  
## <a name="length-validation-is-not-performed-on-a-data-element-in-a-generated-instance-that-is-pulled-from-an-enum-list-in-the-schema"></a>La validation de la longueur n'est pas exécutée sur un élément de données d'une instance générée extraite d'une liste d'énumération dans le schéma  
 Lorsqu'une instance est générée à partir d'un schéma et que les valeurs d'énumération d'un élément de données du schéma ne sont pas conformes à la longueur requise, l'instance peut être générée avec un élément de données provoquant l'échec de la validation XSD en raison de l'impératif de longueur. La validation de schéma ne vérifie pas si une valeur de l'instance générée extraite d'une liste d'énumération du schéma correspond à la longueur minimale/maximale requise.  
  
## <a name="validate-schema-may-not-detect-an-invalid-transaction-set-id-code"></a>La validation du schéma peut ne pas détecter un code d'ID de document informatisé non valide  
 Lorsque vous validez un schéma avec la commande valider le schéma dans la fenêtre de l’Explorateur de solutions de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], la vérification du nœud racine peut ne pas détecte une transaction non valide défini le code de l’ID dans la dernière partie du nœud référence de racine (au format X12_\< Document\>_TSID). Si le TSID du nœud référence de racine du schéma est identique au TSID du nœud d'énumération de l'élément ST01 du schéma, l'opération de validation du schéma ne détecte pas que le TSID n'est pas valide.  
  
## <a name="visual-studio-must-be-restarted-to-make-an-enum-change-in-a-schema-effective-for-instance-validation"></a>Il est nécessaire de redémarrer Visual Studio pour que la modification de l'énumération d'un schéma soit effective lors de la validation de l'instance  
 Si vous modifiez une liste d'énumération d'un schéma, enregistrez ce dernier, puis procédez à la validation de l'instance, BizTalk Server exécute une validation basée sur la version précédente du schéma, et non sur la dernière version. BizTalk Server n'utilise la dernière version du schéma qu'après le redémarrage de Visual Studio.  
  
## <a name="the-edi-instance-properties-dialog-box-may-be-displayed-when-not-needed-in-the-testmap-operation"></a>La boîte de dialogue Propriétés de l'instance EDI peut s'afficher alors qu'elle n'est pas nécessaire dans l'opération TestMap  
 BizTalk Server affiche une boîte de dialogue Propriétés de l’Instance EDI à deux reprises au cours du processus TestMap : une fois afin que vous pouvez entrer les délimiteurs nécessaires pour l’interprétation de l’instance de message d’entrée et une fois pour entrer les délimiteurs pour générer le message de sortie instance. BizTalk Server doit afficher la boîte de dialogue Propriétés de l'instance EDI à deux reprises uniquement et pour les seuls schémas EDI. Il peut toutefois arriver que celle-ci soit affichée à plusieurs reprises pour les schémas autres que EDI. Dans ce cas, fermez la boîte de dialogue.  
  
## <a name="validation-of-an-xml-preserved-interchange-is-not-supported"></a>La validation d'un échange préservé XML n'est pas prise en charge  
 Lors de la validation d’un échange préservé, si vous sélectionnez XML pour le **Type valider l’entrée d’Instance** propriété, l’opération échoue et rien n’est renvoyé. Toutefois, si vous sélectionnez **natif** pour le **Type valider l’entrée d’Instance** lorsque vous validez un échange conservé, l’opération réussira.  
  
## <a name="an-instance-generated-for-a-hipaa-278-schema-will-contain-both-request-and-response-sections"></a>Une instance générée pour un schéma HIPAA 278 contient des sections de requête et de réponse  
 Le schéma HIPAA 278 est utilisé pour les messages de requête et de réponse 278. Si vous utilisez la commande Générer l'instance sur un schéma 278, l'instance générée est associée à des sections de requête et de réponse qui ne doivent jamais être envoyées. Pour créer un message de requête ou de réponse 278 utilisable, ouvrez l'instance générée par les outils XML dans un éditeur de texte, puis supprimez l'une des sections. Vous pouvez par exemple supprimer la section de réponse d'un message de requête.  
  
 Si vous exécutez la commande Valider l'instance sur un message 278 associé à des sections de requête et de réponse, ce dernier est validé correctement par rapport au schéma 278.  
  
## <a name="an-xml-instance-generated-from-a-278-hipaa-schema-will-fail-validation"></a>La validation d'une instance XML générée à partir d'un schéma 278 HIPAA échoue  
 Si vous utilisez la commande Génération d'instance pour générer une instance XML à partir d'un schéma 278 HIPAA, puis la commande Validation d'instance pour valider l'instance, BizTalk Server génère une erreur.  
  
## <a name="a-native-instance-generated-from-a-837-schema-incorrectly-sets-gs08"></a>Une instance native générée à partir d'un schéma 837 définit GS08 de manière incorrecte  
 Lors de la génération d’une instance native en utilisant un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution qui contient le X12_BatchSchema, ainsi qu’un schéma 837I, 837d ou 837p, la valeur de GS08 contient 00401. Avant de traiter cette instance, vous devez modifier la valeur de GS08 à la valeur correcte pour l’instance de schéma.  Le tableau suivant indique la valeur GS08 correcte pour chaque schéma 837 :  
  
|Schéma HIPAA|Valeur GS08|  
|------------------|----------------|  
|837I|004010X096A1|  
|837D|004010X097A1|  
|837P|004010X098A1|  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes connus avec le traitement EDI](../core/known-issues-with-edi-processing.md)   
 [Les Extensions de l’outil XML à l’aide de](../core/using-the-xml-tool-extensions.md)   
 [À l’aide d’outils au moment du Design XML](../core/using-design-time-xml-tools.md)