---
redirect_url: /biztalk/core/adding-biztalk-adapter-for-jd-edwards-oneworld/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: d65b87fbcbdaf89289406ae6850b70c605123451
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-create-send-ports-for-jd-edwards-oneworld"></a><span data-ttu-id="a1064-101">Création de ports d'envoi pour JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="a1064-101">How to Create Send Ports for JD Edwards OneWorld</span></span>
<span data-ttu-id="a1064-102">La procédure suivante permet de créer un port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="a1064-102">Use the following procedure to create a send port.</span></span>  
  
### <a name="to-create-a-send-port"></a><span data-ttu-id="a1064-103">Pour créer un port d’envoi</span><span class="sxs-lookup"><span data-stu-id="a1064-103">To create a send port</span></span>  
  
1.  <span data-ttu-id="a1064-104">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis accédez à la application requise.</span><span class="sxs-lookup"><span data-stu-id="a1064-104">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then navigate to the required application.</span></span>  
  
2.  <span data-ttu-id="a1064-105">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="a1064-105">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a1064-106">Vous pouvez également utiliser **Port statique unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="a1064-106">You can also use **Static One-Way Port**.</span></span>  
  
3.  <span data-ttu-id="a1064-107">Dans le **propriétés de Port d’envoi** boîte de dialogue le **nom** , tapez le nom du port d’envoi (par exemple, tapez **SendToJDE**.)</span><span class="sxs-lookup"><span data-stu-id="a1064-107">In the **Send Port Properties** dialog box, in the **Name** field, type a send port name (for example, type **SendToJDE**.)</span></span>  
  
4.  <span data-ttu-id="a1064-108">Dans le **Type** la liste déroulante, sélectionnez **JDEOneWorld**.</span><span class="sxs-lookup"><span data-stu-id="a1064-108">In the **Type** drop-down list, select **JDEOneWorld**.</span></span>  
  
5.  <span data-ttu-id="a1064-109">Dans le **URI** liste déroulante, sélectionnez le Gestionnaire d’envoi.</span><span class="sxs-lookup"><span data-stu-id="a1064-109">In the **URI** drop-down list, select the send handler.</span></span>  
  
6.  <span data-ttu-id="a1064-110">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a1064-110">Click **OK**.</span></span>  
  
