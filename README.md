# Modèles d'inférence de Silvergrain Studio

Ce dépôt héberge, en **releases**, les paquets de modèles d'inférence que
Silvergrain Studio télécharge à la demande, quand l'éditeur du modèle ne publie
pas lui-même un fichier que le produit sait exécuter. Chaque paquet est un
`.dtmodel` : une archive ZIP contenant un `config.json` de provenance et un ou
plusieurs graphes ONNX. Le produit vérifie l'empreinte SHA-256 de chaque paquet
à l'arrivée, épinglée dans son catalogue : un fichier différent n'est jamais
installé.

Tous les poids servis ici sont sous licence **permissive** (Apache-2.0 ou MIT),
relevée sur la carte de modèle ou la concession écrite de l'éditeur, jamais
seulement sur l'étiquette d'un dépôt. La provenance complète de chaque paquet
est dans son `config.json` et dans les notes de sa release.

## Paquets

| Release | Fichier | Contenu | Licence des poids | Origine |
|---|---|---|---|---|
| `profondeur-depth-anything-v2-small-1.0` | `profondeur-depth-anything-v2-small.dtmodel` (91 850 964 octets) | Depth Anything V2 Small (ViT-S), profondeur relative ; export ONNX non modifié | Apache-2.0 (Small seulement) | Depth Anything V2 — `DepthAnything/Depth-Anything-V2` ; export ONNX `onnx-community/depth-anything-v2-small` |
| `paysage-detr-panoptique-1.0` | `paysage-detr-panoptique.dtmodel` (159 523 234 octets) | DETR ResNet-50 panoptique (COCO panoptique, 250 catégories), export ONNX non modifié | Apache-2.0 | DETR, Facebook AI Research — `facebookresearch/detr` ; export ONNX `Xenova/detr-resnet-50-panoptic` |
| `generatif-moebius-1.0` | `generatif-moebius.dtmodel` (1 248 192 828 octets) | dénoiseur de Moebius (graphe réécrit sans Einsum ni Conv3d, fp32, 912 Mo), encodeur et décodeur VAE ; boucle DDIM hors graphe, portée par le produit | Apache-2.0 (Moebius) et MIT (VAE) | Moebius, HUST Vision Lab, ECCV 2026 — `hustvl/Moebius`, point de contrôle `pretrained` ; VAE `madebyollin/sdxl-vae-fp16-fix` tel que servi par `hustvl/PixelHacker` |

Le paquet des masques de visage (MediaPipe Face Landmarker converti en ONNX,
Apache-2.0) suivra le même chemin, sous la release `face-landmarks-mediapipe-1.0`.

## Attribution

Les poids de Moebius sont l'œuvre du HUST Vision Lab, sous Apache License,
Version 2.0, avec une concession écrite d'usage commercial des poids et des
images produites ; le VAE est celui de `madebyollin/sdxl-vae-fp16-fix` (MIT),
dérivé de `stabilityai/sdxl-vae` (MIT). L'export ONNX, la réécriture du
dénoiseur et l'empaquetage sont de Silvergrain (Selim Allee EI). Voir `NOTICE`.
