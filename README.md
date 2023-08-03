# Custom Diffusion + Attend and Excite
Low cost customization of stable diffusion model using custom diffusion along with attend and excite

Personalization is a vital aspect for every organization as it allows them to create a distinct and unique identity for their products or services. Each company strives to develop a look and feel that sets them apart from competitors and cannot be easily replicated without permission. For instance, companies like Nike and Reebok market shoes, but their designs and aesthetics are markedly different and proprietary to each brand. These unique elements are crucial for establishing brand identity and attracting customers.

Our approach aims to preserve the fidelity of custom concepts while also ensuring a proper binding of colour with the entity when applicable. To achieve this, we refrain from using a regularized dataset, which allows us to significantly reduce training time without compromising the quality of the generated images. 

By avoiding regularization, our model can focus on capturing the intricate details and unique characteristics of each custom concept in the dataset. This increased flexibility enables the model to produce high-fidelity representations of the custom objects, maintaining their original style and shape accurately. 

Furthermore, in cases where the prompt contains an association of an entity with a specific colour, our method ensures that the generated image accurately reflects this colour binding. By attending to relevant features and using an "attend and excite" mechanism, the model can faithfully incorporate the intended colour associations into the generated images. 

The exclusion of regularization not only improves the image quality but also leads to a notable reduction in training time. Without the added constraints, the model can explore a broader range of variations efficiently, accelerating the overall generation process. 

In summary, our approach successfully maintains the fidelity of custom concepts while ensuring accurate colour bindings, all without the need for a regularized dataset. This results in both improved image quality and reduced training time, making our method a powerful and efficient solution for custom concept generation.

_____________________________________________________________________________________________________________________________________________________________________________
# Fine tune the model using custom diffusion
1. To generate custom concepts clone the custom diffusion repository:https://github.com/adobe-research/custom-diffusion

2. To run the model without regularization dataset follow the steps:
3. Delete the parameters --reg_datapath and --reg_captions from scripts/finetune_real.sh
4. Add the parameter --repeat 100 to the file
5. save the file

6. If you are running in a10g then and --batch_size 2 in scripts/finetune_real.sh.
7. Run the scripts/finetune_real.sh as per stated in the custom diffusion repository.

8. To run the model without regularixation dataset for multiple concepts,make he same chnages as done for single concept in scripts/finetune_joint.sh

_________________________________________________________________________________________________________________
# Convert .ckpt to .bin

1. pip install accelerate
2. pip install transformers>=4.25.1
3. If the tranformer version is still below 4.25.1 the use pip install --upgrade transformers
4. Now once the .ckpt files of the model parameters are obtained, we convert it to .bin using the following command:
5. python src/convert.py --delta_ckpt <path-to-folder>/delta_model.ckpt --ckpt <path-to-model-v1-4.ckpt> --mode compvis-to-diffuser                  
_________________________________________________________________________________________________________________________________

# Run CD+AE
1. conda env create -f environment/environment.yaml
2. conda activate ldm2
3. Add ldm2 conda environmet to the kernal to run the ipython notebooks.
4. upload the .bin  model file in the load fuction in the Custom.ipynb notebook
5. Execute Attend-and-Excite/notebooks/Custom.ipynb to obtain the images.
_________________________________________________________________________________________________________________________________
 Th model weights for some concepts are in Attend-and-Excite/notebooks/weights/logs 
   

 
 
