# Reproduction levels

1. `python verify_release.py`: verified on the downloaded public artifact;
   checks hashes, table arithmetic and recorded paired input identities.
2. Offline mask metrics: source evaluators and per-instance/edge records are
   provided. Recomputing mask AP additionally needs the exact original model
   predictions/checkpoints and provider ground truth, absent from this release.
3. Full GPU reruns: not executed on a fresh machine. The observed environment
   was Python 3.8, PyTorch 1.9, CUDA 11.1, AdelaiDet/Detectron2 and RTX 3090.
   Sources are execution snapshots, not a complete installed dependency tree.

For a GPU rerun, obtain provider data and permitted ImageNet initialization,
install the recorded dependency versions, reconstruct the archived split,
relocate `/WORKSPACE` and `/LOCAL_HOME` paths, and run isolated engineering
checks before training. Preserve image/box/category-only training; masks belong
to offline scoring. Use the recorded seeds, schedules and final-only rule.
Never silently compare an optimized implementation to an original baseline
from a different run or replace a negative seed with a more favorable result.

M18K V1: https://github.com/abdollahzakeri/m18k
StrawDI: https://strawdi.github.io/
MinneApple: https://rsn.umn.edu/projects/orchard-monitoring/minneapple
AdelaiDet: https://github.com/aim-uofa/AdelaiDet
BoxTeacher: https://github.com/hustvl/BoxTeacher
