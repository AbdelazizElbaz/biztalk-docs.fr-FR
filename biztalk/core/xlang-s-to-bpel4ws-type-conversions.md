---
title: Conversions de Type XLANG-s en BPEL4WS | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XLANG/s
- XLANG/s, warning
- XLANG/s, BPEL4WS
- XLANG/s, converting
ms.assetid: a35d4dba-9344-43c8-86e6-a373a4452579
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02412b86b8649b73cadb4715793f085682a1de74
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="xlang-s-to-bpel4ws-type-conversions"></a>XLANG-s pour les Conversions de Type BPEL4WS
Les tableaux suivants présentent les conversions entre diverses constructions XLANG/s et BPEL4WS.  
  
> [!CAUTION]
>  XPath 1.1 ne prend pas en charge les nombres au format exponentiel ou double. Les valeurs littérales de ces formats dans les orchestrations XLANG/s sont exportées vers BPEL4WS à l'aide du format %f, et une perte de précision peut en résulter.  
  
## <a name="literals-if-the-literal-is-part-of-an-expression"></a>Littéraux (si le littéral fait partie d'une expression)  
  
|XLANG/s|BPEL4WS|  
|--------------|-------------|  
|Chaîne, caractère|Chaîne XPath|  
|Entier, réel|Nombre XPath|  
|Booléen "true", "false"|Fonctions XPath true(), false()|  
  
## <a name="literals-standalone-assignment"></a>Littéraux (assignation autonome)  
  
|XLANG/s|BPEL4WS|  
|--------------|-------------|  
|Constante littérale|Équivalent XSD|  
  
## <a name="variables"></a>Variables  
  
|XLANG/s|BPEL4WS|  
|--------------|-------------|  
|Référence de variable|bpws:getContainerData(%varName%,  part, %locationPath%)|  
|Référence de message (type .NET)|getContainerData(%msgName%, part, %locationPath%)|  
|Référence de partie de message|bpws:getContainerData(%msgName%, %locationPath%)|  
|Référence de champ distinctif|bpws:getContainerData(%msgName%, %partName%, %locationPath%)|  
|Référence de propriété de données de message|bpws:getContainerProperty(%msgName%, %propertyQName%)|  
  
## <a name="operators"></a>Opérateurs  
  
|XLANG/s|BPEL4WS|  
|--------------|-------------|  
|Unaire +|Ignoré|  
|Opérateur unaire -|Moins unaire XPath|  
|Unaire !|Fonction XPath not()|  
|Binaire & &,&#124;&#124;|Opérateurs XPath 'and', 'or'|  
|Binaire ==, !=, <=, <, >=, >|XPath '=', '! =', ' < =', ' <', ' > =', ' >' opérateurs|  
|Binaire +, -, *, % avec les deux opérandes de type intégral|Opérateurs XPath '+', '-', '*', 'mod'|  
  
## <a name="xlangs-constructs-that-are-disallowed-in-bpel4ws"></a>Constructions XLANG/s non autorisées dans BPEL4WS  
  
-   Référence de propriété de contexte de message  
  
-   Référence de propriété de service  
  
-   Référence de propriété de port  
  
-   Référence de propriété de liaison de service  
  
-   Unaire - de type non intégral  
  
-   Unaire ~  
  
-   Opérateur de conversion  
  
-   Binaire / avec opérandes de type intégral  
  
-   Binaire +, -, *, %, / avec opérandes de type non intégral  
  
-   Binaire <=, <, >=, > avec opérandes de type non chaîne  
  
-   Opérateurs de bits &, ^,&#124;  
  
-   Opérateurs de décalage <<, >>  
  
-   Expression vérifiée  
  
-   Expression intrinsèque  
  
-   Antérieur et postérieur à l'incrémentation et la décrémentation ++, --  
  
-   Appel d'objet (paramètres de référence avec ou sans ou et/ou)  
  
-   Opérateur 'new'