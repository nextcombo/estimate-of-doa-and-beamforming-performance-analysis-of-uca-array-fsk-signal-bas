# Estimate of DoA and Beamforming Performance Analysis of UCA Array FSK Signal Based on Mutual Coupling Effects [with MATLAB Code]

2. System Model 2.1 Array Geometry and Signal Model Considering a uniform circular array (UCA) composed of an array of isotropic elements, with the array radius. Assuming the carrier frequency is and the wavelength is. The array element position coordinates of UCA can be represented as:
The azimuth angle of the ith element is indicated here.
Received signal model assumes the existence of a source with both desired and interfering signals. The received baseband signal matrix can be represented as:
The array manifold vectors, the transmitted signal waveform, and additive Gaussian white noise are involved.
2.2 Mutual coupling effect modeling in actual antenna arrays, the electromagnetic mutual coupling between elements will change the array's receiving characteristics. The effect is modeled in the code by calculating the mutual impedance matrix. Set as impedance matrix, the mutual coupling matrix is defined as:
The final model of the received signal with mutual coupling is revised to:.
3. The waveform direction estimation algorithm code implements four DoA estimation algorithms, among which the knowledge-based KW algorithm utilizes known waveform information and has its unique advantages.
3.1 Delayed summation conventional beamforming method, by scanning spatial angles to find the maximum output power:
3.2 Minimum variance undistorted response: under the constraint of maintaining the desired directional gain, minimize the array output power
The code employs diagonal loading technology to handle the inverse problem of covariance matrix.
3.3 Multiple Signal Classification (MUSIC) utilizes the orthogonality of signal subspace and noise subspace:
3.4 The KW algorithm, based on known waveforms, differs from subspace methods that rely solely on statistical characteristics. The KW algorithm utilizes the known transmitted waveform (training sequence) for non-coherent parameter estimation. This method is primarily composed of three steps:
(1) Spatial Feature Matrix Estimation The algorithm first calculates the cross-correlation matrix and the auto-correlation matrix of the known signal:
Utilizing the Wiener filtering principle, estimate the spatial feature matrix (coded as Bhat) that contains channel information.
The Tikhonov regularization parameter is used to prevent the matrix from being ill-conditioned. The column vectors of this matrix are approximately equal to the array manifold vector multiplied by a complex gain.
(2) Phase difference vector construction for the ith source, extracting its estimated spatial feature vector. To eliminate phase smearing and utilize the circular symmetry geometric properties of UCA, the algorithm constructs a phase difference vector.
Define the baseline (element spacing), and calculate the phase difference between pairs of elements:
The first index is for the radial position of the element, and the second index is for the relative displacement on the circle. The code stacks multiple values to increase the robustness of the estimated phase difference.
(3) Solution of the least square parameters based on UCA's geometric manifold, phase difference between antenna elements and wave arrival direction has a linear relationship. Constructing a linear system:
The matrix is constructed from the array of elements, with rows corresponding to the spatial frequency vectors to be estimated.
Solving for the parameter vector using least squares:
The final recovery of the inclination and azimuth angles:
This method utilizes known waveform information to effectively decouple channel estimation and angle estimation, typically exhibiting better robustness than subspace methods under low signal-to-noise ratio or limited number of fast samples.
4. Beamforming and signal demodulation After obtaining the DoA estimation, the system performs beamforming to separate the desired signals and suppress interference.
4.1 The beamforming weight calculation simulation mainly compares two types of beamformers:
★  
DAS Beamformer:
★  
MVDR Beamformer:
4.2 Perform FSK demodulation on the signal after beamforming, and calculate the following key indicators:
★  
Bit Error Rate (BER): Measures the ability to suppress interference.
★  
Error Vector Magnitude (EVM): Measuring the quality of signal demodulation.
5. Conclusion The code has realized a complete communication link simulation, from the inter-coupling modeling at the physical layer to the DoA estimation and beamforming at the signal processing layer. Particularly, the KW algorithm provides a high-precision angle estimation scheme by combining prior knowledge of known waveforms. By comparing the RMSE, BER, and EVM of different algorithms under ideal and coupled environments, we can quantitatively evaluate the performance boundaries of array systems and the robustness of algorithms.

## Images

![DoA Estimation and Beamforming Performance Analysis of UCA Array FSK Signal Based on Mutual Coupling Effects [with MATLAB Code]](01.jpg)
![DoA Estimation and Beamforming Performance Analysis of UCA Array FSK Signal Based on Mutual Coupling Effects [with MATLAB Code]](02.jpg)
![DoA Estimation and Beamforming Performance Analysis of UCA Array FSK Signal Based on Mutual Coupling Effects [with MATLAB Code]](03.jpg)
![DoA Estimation and Beamforming Performance Analysis of UCA Array FSK Signal Based on Mutual Coupling Effects [with MATLAB Code]](04.jpg)

<!-- PAYMENT_BLOCK -->

## Get this dataset

- Payment link (Stripe): [Buy now](https://buy.stripe.com/3cs8yP7sY87d0vu9AB)
- Payment QR code: ![Payment QR code](pay.png)

<!-- /PAYMENT_BLOCK -->
