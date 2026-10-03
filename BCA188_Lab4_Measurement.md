1. Potentiometer Readings

| Position | Expected Raw ADC | Actual Raw ADC |
|---|---:|---:|
| Minimum | 0 | 0 |
| Low | 1023.75 | 1023 |
| Middle | 2047.50 | 2046 |
| High | 3072.25 | 3072 |
| Maximum | 4095 | 4095 |

2. PWM Duty

| Position | Raw ADC | PWM Code | PWM Duty |
|---|---:|---:|---:|
| Minimum | 0 | 0 | 0% |
| Low | 1023 | 64 | 25.1% |
| Middle | 2046 | 127 | 49.8% |
| High | 3072 | 192 | 75.3% |
| Maximum | 4095 | 255 | 100% |

4. Oscilloscope Comparison

| Pin | Signal | Observation |
|---|---|---|
| GPIO19 | PWM | Digital square-wave; duty cycle changes |
| GPIO25 | DAC | Analog voltage level changes |

Oscilloscope was not available, so GPIO19 and GPIO25 were not directly compared using an oscilloscope.

5. Explanation

Why PWM is not the same as DAC PWM produces? a rapidly switching digital HIGH/LOW waveform. Changing the PWM duty cycle changes how long the signal stays HIGH during each period. A DAC instead produces an analog voltage level corresponding to its digital code. Therefore, a PWM measurement on GPIO19 should not be reported as a DAC voltage measurement on GPIO25.
Why an ADC endpoint may saturate? The 12-bit ADC has a nominal range of 0–4095. When the input reaches the upper measurable range, the ADC cannot represent a higher value, so the reading remains near 4095 even if the input increases further. This is called saturation. The same principle applies near the lower endpoint.
