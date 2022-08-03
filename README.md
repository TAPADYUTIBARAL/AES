# AES
AES_CPA &amp; AES_DOM 
//Download the trace_189 file and added the trace location in the respected code.




Approach for Implementation - CPA 10th Round Key Extraction
Since it is proposed to extract the 10th round key using power traces provided, the approach is to perform an analysis of the back propagation of the cipher, till the S-BOX. 3 input files are provided to us: Trace Files - Contains 1000 traces, each with 12000 sample points for different inputs, textin_array - Contains input files (plaintext) with 1000 inputs (rows) of 128 bit (16 byte) each, textout_array - Contains the cipher text received after the AES is performed on the input files.

The textout_array file will be used as the cipher text file for the back propagation.

Keyguesses will be made for each subkey. Each keyguess byte will be ex-ored with the corresponding position byte of the cipher text, for all output rows.

In AES, this step is preceeded by the Shift Rows operation in the 10th round (there is no Mixed Column operation in the 10th round). However, since the shift row does not change the value but only its position, this may be ignored in the implementation for the test project. Since the propagation of key extraction is flowing backwards, the inverse shift row function should be performed. However since the function does not change value but only position in the list, it may be dropped

Similarly, the SBox operation preceeds the Shift Row function.Therefore, in back propagation, inverse S-Box has to be performed to arrive at the correct stage where CPA can be done with the power traces. SInce the S-Box is the non-linear function of the AES implementation, CPA is performed with tangible results in this phase.

From the power traces (trace_array), we notice that the 10th round does not have the mixed column in implementation. Therefore, as observed from the traces, the sample points 9550 to 9700 depict the s-box operations against which we would like to correlate.


exit()
