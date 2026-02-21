# Optional Local Setup (Conda + AI Help)

Use Binder for the smoothest course experience.
Use local setup only if you prefer running notebooks on your own machine.

## Binder vs Local

- Use **Binder** when you want zero setup and fast onboarding.
- Use **Local Conda** when you want persistent files, custom tooling, or offline edits.
- Use **Colab** for Lab 4 (neural networks), where GPU support is helpful.

## Local Setup (Step-by-Step)

1. Install Miniconda: https://www.anaconda.com/docs/getting-started/miniconda/main
2. Clone this repository:
   ```bash
   git clone https://github.com/wfondrie/ushupo-ml-short-course.git
   cd ushupo-ml-short-course
   ```
3. Create/update the environment:
   ```bash
   make env
   ```
4. Activate the environment:
   ```bash
   conda activate ./envs
   ```
5. Launch Jupyter Lab:
   ```bash
   make jupyter
   ```

## Sanity Check

After Jupyter opens:

1. Open `notebooks/1_introduction.ipynb`.
2. Run all cells from a fresh kernel.
3. Confirm there are no import errors and plots render correctly.

If a notebook needs project data, run:

```bash
make data
```

## Troubleshooting Quick Notes

- `conda: command not found`: close/reopen terminal after Miniconda install, then retry.
- Wrong kernel/interpreter: in Jupyter, switch kernel to the env created from `./envs`.
- Binder is slow to start: wait for image build to finish, then refresh once.
- Package mismatch after edits: rerun `make env` to resync dependencies from `environment.yml`.

## Prompt Template for AI Tools

Use this when asking for setup help:

> I am using the `wfondrie/ushupo-ml-short-course` repo.
> Please guide me step-by-step to run notebooks with Conda using `make env`, `conda activate ./envs`, and `make jupyter`.
> Assume I am a beginner. Ask me to run one command at a time and verify each output before moving on.
