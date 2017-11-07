---
title: "Problèmes connus avec la génération de schéma et de Validation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df1eaa6c-0d3e-4aec-9de0-8b9817b7bb97
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a462ab04aad857bf87b189cafce14bb9c3747e8
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="known-issues-with-schema-generation-and-validation"></a><span data-ttu-id="de90e-102">Problèmes connus avec la Validation et génération de schéma</span><span class="sxs-lookup"><span data-stu-id="de90e-102">Known Issues with Schema Generation and Validation</span></span>
<span data-ttu-id="de90e-103">Cette rubrique fournit des informations concernant les problèmes connus en matière de génération et de validation de schéma.</span><span class="sxs-lookup"><span data-stu-id="de90e-103">This topic provides information about known issues with schema generation and validation.</span></span>  
  
## <a name="an-instance-message-generated-for-a-positional-record-with-tags-could-be-incorrect"></a><span data-ttu-id="de90e-104">Un message d'instance généré pour un enregistrement positionnel doté de balises est peut-être incorrect</span><span class="sxs-lookup"><span data-stu-id="de90e-104">An instance message generated for a positional record with tags could be incorrect</span></span>  
 <span data-ttu-id="de90e-105">Dans les enregistrements positionnels, la balise peut se trouver dans un champ ou s'étendre entre des champs.</span><span class="sxs-lookup"><span data-stu-id="de90e-105">For positional records, the tag can be within a field or can span between fields.</span></span> <span data-ttu-id="de90e-106">Dans les deux cas, l'instance générée ne sera pas valide et provoquera un échec dans le moteur d'analyse au cours de l'étape d'analyse.</span><span class="sxs-lookup"><span data-stu-id="de90e-106">In either case, the instance generated will not be valid and will cause a failure in the Parsing Engine during the parsing stage.</span></span>  
  
 <span data-ttu-id="de90e-107">Si la balise ne fait partie d'aucun enfant (enregistrements enfants ou champs enfants), ce problème ne se produira pas.</span><span class="sxs-lookup"><span data-stu-id="de90e-107">If the tag is not part of any children (child records or child fields), this problem will not occur.</span></span>  
  
 <span data-ttu-id="de90e-108">Pour résoudre ce problème, incluez la valeur réelle de la balise comme valeur par défaut dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="de90e-108">To work around this issue, include the actual value of the tag as the default in the schema.</span></span> <span data-ttu-id="de90e-109">Dans l’extension de fichier plat de l’Éditeur BizTalk, vous pouvez définir le **valeur fixe** ou **valeur par défaut** propriété du champ positionnel approprié avec la valeur de la balise.</span><span class="sxs-lookup"><span data-stu-id="de90e-109">In the flat file extension of the BizTalk Editor, you can set the **Fixed Value** or **Default Value** property of the appropriate positional field with the value of the tag.</span></span>  
  
## <a name="an-instance-message-generated-for-a-field-with-some-restrictions-may-not-pass-validation"></a><span data-ttu-id="de90e-110">Un message d'instance généré pour un champ avec certaines restrictions risque de ne pas être validé</span><span class="sxs-lookup"><span data-stu-id="de90e-110">An instance message generated for a field with some restrictions may not pass validation</span></span>  
 <span data-ttu-id="de90e-111">Lorsque vous générez un message d’instance à partir d’un schéma qui contient un ou plusieurs **Fieldelement** et **attribut de champ** nœuds qui ont des types de données qui ont été dérivées à l’aide du mécanisme de restriction, comme Lorsque le **modèle** propriété est utilisée, les exemples de données générés pour ces champs n’est peut-être pas conforme aux exigences de la restriction, ce qui empêche la validation réussie de ce message d’instance à l’aide du même schéma à partir de qu’il a été généré.</span><span class="sxs-lookup"><span data-stu-id="de90e-111">When you generate an instance message from a schema that contains one or more **Field Element** and **Field Attribute** nodes that have data types that have been derived using the restriction mechanism, such as when the **Pattern** property is used, the sample data generated for such fields may not conform to the requirements of the restriction, thereby preventing successful validation of that instance message using the same schema from which it was generated.</span></span>  
  
## <a name="an-instance-message-generated-for-a-schema-that-contains-an-infinite-loop-may-not-be-valid"></a><span data-ttu-id="de90e-112">Un message d'instance généré pour un schéma qui contient une boucle infinie n'est peut-être pas valide</span><span class="sxs-lookup"><span data-stu-id="de90e-112">An instance message generated for a schema that contains an infinite loop may not be valid.</span></span>  
 <span data-ttu-id="de90e-113">Votre schéma peut contenir une boucle infinie lorsqu’elle contient une référence circulaire à un nœud avec un **Min Occurs** valeur supérieure ou égale à un, empêchant essentiellement une condition d’arrêt de la propriété.</span><span class="sxs-lookup"><span data-stu-id="de90e-113">Your schema can contain an infinite loop when it contains a circular reference to a node with a **Min Occurs** property value greater than or equal to one, essentially preventing a termination condition.</span></span> <span data-ttu-id="de90e-114">La génération du message d'instance s'arrêtera artificiellement afin que l'opération de génération puisse se terminer, mais le message d'instance produit ne sera par conséquent pas conforme au schéma à partir duquel il a été généré.</span><span class="sxs-lookup"><span data-stu-id="de90e-114">Instance message generation will artificially terminate so that the generation operation can complete, but the produced instance message will thereby not conform to the schema from which it was generated.</span></span> <span data-ttu-id="de90e-115">Ce type de schéma est généralement suspect.</span><span class="sxs-lookup"><span data-stu-id="de90e-115">Such schemas are usually suspect.</span></span>  
  
## <a name="validation-of-xml-instance-fails-for-document-schema-which-has-the-target-namespacehttpwwww3orgxml1998namespace"></a><span data-ttu-id="de90e-116">La validation de l'instance XML a échoué pour le schéma de document dont l'espace de noms cible est « http://www.w3.org/XML/1998/namespace ».</span><span class="sxs-lookup"><span data-stu-id="de90e-116">Validation of XML instance fails for document schema which has the target namespace="http://www.w3.org/XML/1998/namespace"</span></span>  
 <span data-ttu-id="de90e-117">Le lien hypertexte « http://www.w3.org/XML/1998/namespace » est un espace de noms réservé dont le préfixe doit être « XML ».</span><span class="sxs-lookup"><span data-stu-id="de90e-117">The HYPERLINK "http://www.w3.org/XML/1998/namespace" is a reserved namespace whose prefix should be “XML”.</span></span> <span data-ttu-id="de90e-118">Vous pouvez modifier manuellement le préfixe et utiliser « XML ».</span><span class="sxs-lookup"><span data-stu-id="de90e-118">You can manually edit the prefix to “XML”.</span></span>

## <a name="see-also"></a><span data-ttu-id="de90e-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de90e-119">See also</span></span>
<span data-ttu-id="de90e-120">Plus d’informations sur ces propriétés [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="de90e-120">More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
