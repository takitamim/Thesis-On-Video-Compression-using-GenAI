# Neural Video Compression with Generative AI

Research code for my RUET undergraduate thesis, **Learning-Based Ultra-Low-Bitrate Video Compression Using Generative AI**.

## Start here

- `calculate_prediction_time.py`: load the GOP-8 checkpoint and measure frame-prediction time.
- `delta_t_calculate.py`: combine predictions with VVC encoder logs to calculate encoding-time savings.
- `calculate_prediction_time_gop4.py` and `delta_t_calculate_gop4.py`: the separate GOP-4 pipeline.
- `.github/workflows/`: manually triggered evaluation workflows.
- `Archive/VVC Reconstructed/`: evaluation inputs and encoder outputs.

## Run the evaluation

Use Python 3.11 (the version used in the included CI workflows). Create a virtual environment, install PyTorch for your CPU/CUDA environment, then:

```bash
python -m pip install -r requirements-ci.txt
python calculate_prediction_time.py
python delta_t_calculate.py
```

For GOP-4, run the matching `_gop4.py` pair. Do not mix their output directories. The scripts default to the repository folder; `THESIS_ROOT` overrides the root and `MEASURE_CLASS` optionally selects one test class. Checkpoint files and the expected `recon.yuv` / `encode.log` inputs must be present. Timings depend on hardware, warmup and runtime environment.

## Research context

The résumé reports a 3.4M-parameter U-Net/ConvLSTM model, a 20,000-sample Inter4K training dataset, evaluation on 13 JVET sequences, 6–7% bitrate reduction, BD-BR of −5.36%, and 8.51% encoding-time savings. These are reported thesis results, not automatically reproduced by browsing this repository. This checkout exposes the evaluation pipeline; it is not a complete training package.

Supervisor: Md. Zahirul Islam, Assistant Professor, CSE, RUET.
