---
title: Codes de fin utilisateur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- trailers [SWIFT]
- SWIFT, trailers
ms.assetid: 340d9fc8-467b-4cba-b69f-eb761767deaa
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff907e262088acd188028282fe2e03441071358a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="user-trailers"></a>Codes de l’utilisateur
Codes de fin utilisateur, à l’exception du code de fin CHK, sont facultatifs et lorsqu’il est présent, se produisent dans l’ordre suivant :  
  
|Code de fin du code|Nom|  
|------------------|----------|  
|MAC|Code d’authentification de message|  
|PAC|Code d’authentification propriétaire|  
|CHK|Somme de contrôle|  
|TNG|Formation|  
|PDE|Émission de double possible|  
  
-   **Code de fin Message Authentication Code (MAC).** Autorise l’authentification par l’utilisateur destinataire. Le code de fin MAC est suivie d’un résultat de l’authentification. Ce code de fin est obligatoire pour la plupart des catégories de message de l’utilisateur à l’application de la FIN.  
  
     Lorsque le Service de FIN est utilisé, un code de fin PAC (le cas échéant) suit le code de fin MAC. Le code suivant est un exemple d’un code de fin MAC :  
  
    ```  
    {MAC:<authentication-result>}  
    where <authentication-result> = 8!h  
    ```  
  
-   **Code de fin du Code (PAC) d’authentification propriétaire.** Le code de fin PAC est utilisé dans le service de FIN uniquement lorsque vous utilisez l’option d’authentification double. Messages d’utilisateur à 5 de bloc de FIN incluent le code de fin PAC immédiatement après le code de fin MAC, le cas échéant. Ce résultat est calculé sur les champs extraits du bloc 4 du message, la valeur du champ 115, le cas échéant et le \<résultat de l’authentification\> du code de fin MAC pour les Services de la copie avec l’authentification double.  
  
     Par conséquent, l’indicateur de fin de bloc (CrLf-) est inclus dans le calcul PAC et les champs sont définis comme suit :  
  
    -   Les quatre premiers caractères sont CrLf :  
  
    -   Le champ et le délimiteur sont présents, autrement dit, les 32 a :, 20 :, et ainsi de suite.  
  
    -   Tous les sous-champs et leurs délimiteurs sont présents.  
  
     Le code suivant est un exemple du format de code de fin PAC :  
  
    ```  
    {PAC:[<authentication-result>]}  
    where <authentication-result> is mandatory on input messages only and  
    <authentication-result> = 8!h  
    ```  
  
-   **CHK (somme de contrôle), code de fin (obligatoire pour tous les messages FIN)**  
  
     Le code de fin CHK est obligatoire pour tous les messages FIN et est calculé en fonction des adresse du destinataire (12 caractères avec la neuvième remplacé par *X* ainsi que le bloc de texte). Ce code de fin permet au système et du CBT pour vérifier que les messages ne sont pas endommagées en raison d’un dysfonctionnement du système ou une erreur de transmission non détecté.  
  
     Le code suivant est un exemple du format de code de fin CHK :  
  
    ```  
    {CHK:<checksum-result>}  
    where <checksum-result> = 12!h  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des schémas](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)