 (cd "$(git rev-parse --show-toplevel)" && git apply --3way <<'EOF' 
diff --git a/README.md b/README.md
new file mode 100644
index 0000000000000000000000000000000000000000..d11df5f1c97701da1fa78cbf038c4983886e1919
--- /dev/null
+++ b/README.md
@@ -0,0 +1,33 @@
+# EduColor Focus
+
+EduColor Focus is a Windows-oriented Python desktop utility that applies a subtle, click-through color overlay to the whole screen. It selects a study color mode from explicit rules derived from the provided EEG and cognitive-performance experiment data.
+
+## Features
+
+- CustomTkinter control panel for current condition and learning goal selection.
+- tkinter full-screen overlay using `attributes("-alpha", ...)` and `attributes("-topmost", True)`.
+- Windows click-through support through `WS_EX_TRANSPARENT`, `WS_EX_LAYERED`, and `WS_EX_TOOLWINDOW` extended window styles.
+- Rule-based selection of Focus Booster, High Performance, Brain Reset, and Deep Reading presets.
+- Experimental data stored in dictionaries so future research values can be replaced without rewriting UI code.
+- Focus Booster timer that recommends switching to Brain Reset after 20 minutes.
+- Windows startup registration and optional system tray icon support.
+
+## Install
+
+```bash
+python -m venv .venv
+.venv\Scripts\activate
+pip install -r requirements.txt
+python educolor_focus.py
+```
+
+> The overlay and click-through feature are designed for Windows. On other platforms, the app can still display the UI, but Windows-only features show an explanatory message or become no-ops.
+
+## Preset logic
+
+| Mode | Priority use case | Experimental basis | Default setting |
+| --- | --- | --- | --- |
+| Focus Booster | Short memorization, drowsiness removal | Group B: high-saturation blue, +11.5% focus, +45.0% cognitive load, 96.7% accuracy | `#1E90FF`, alpha 15% |
+| High Performance | Problem solving and test-like work | Group D: +8.9% focus, +5.3% cognitive load, 98.0% accuracy | optimized blue, alpha 10% |
+| Brain Reset | Rest after study and stress management | Group C: -18.4% stress, +33.3% sleepiness index | `#6FA8FF`, alpha 20% |
+| Deep Reading | Concept learning and long reading | Group A + D balance for readability and sustained focus | very low-saturation filter |
 
EOF
)
