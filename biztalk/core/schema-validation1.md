---
title: "Schéma Validation1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 599f1bbb-2af5-4278-8b0f-0e5a6517e8e3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20224a77530139a97647d91b0b46f9384d6c2753
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schema-validation"></a><span data-ttu-id="28205-102">Validation de schéma</span><span class="sxs-lookup"><span data-stu-id="28205-102">Schema Validation</span></span>
<span data-ttu-id="28205-103">Si une extension de l’Éditeur BizTalk fournit un **ISchemaValidator** de l’objet, l’infrastructure appellera **ISchemaValidator.ValidateSchema** lorsque l’utilisateur appelle le **valider le schéma** commande, ou lors de la compilation lorsque l’utilisateur crée le projet BizTalk contenant le schéma.</span><span class="sxs-lookup"><span data-stu-id="28205-103">If a BizTalk Editor extension provides an **ISchemaValidator** object, the framework will invoke **ISchemaValidator.ValidateSchema** when the user invokes the **Validate Schema** command, or during compilation when the user builds the BizTalk project containing the schema.</span></span> <span data-ttu-id="28205-104">L’extension généralement valide les propriétés personnalisées et peut retourner des messages d’erreur sous forme de tableau de **IValidationInfo** objets.</span><span class="sxs-lookup"><span data-stu-id="28205-104">The extension usually validates the custom properties, and can return error messages as an array of **IValidationInfo** objects.</span></span> <span data-ttu-id="28205-105">Les messages d'erreur sont affichés dans la fenêtre Liste des tâches de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], accompagnés d'erreurs renvoyées par le compilateur de l'Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="28205-105">The error messages are displayed in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Task List window, along with errors returned from BizTalk Editor compiler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28205-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28205-106">See Also</span></span>  
 [<span data-ttu-id="28205-107">Extension de l’Éditeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="28205-107">Extending BizTalk Editor</span></span>](../core/extending-biztalk-editor.md)