# 🧠 Medical LLM-as-a-Judge: Automated Evaluation of EHR Summarization using PDSQI-9

This repository provides a Python script and rubric for evaluating large language model (LLM)-generated summaries of electronic health record (EHR) notes using the **Provider Documentation Summarization Quality Instrument (PDSQI-9)**. The PDSQI-9 was developed with construct and content validity using seven human expert raters that evaluated and answered over 8,000 questions on real-world, multi-document EHR notes for LLM-generated summaries.

It enables **automated, consistent, and transparent scoring** of clinical summarization quality across nine dimensions including evaluation of hallucinations, omissions, citations, stigmatizing language, usefulness for a given specialty, and quality of language generated. 

This work supports scalable evaluation of generative AI tools integrated into clinical documentation workflows and contributes to building trustworthy and rigorous AI for healthcare systems.

---

## 🛠 Features

- **PDSQI-9** is a validated rubric for evaluating medical summaries
- Uses LLM-as-a-Judge prompts to assign structured scores on a 1-5 Likert scale with explanations
- Handles multiple note inputs from a series of patient encounters
- JSON-based input and output

---

## 📂 How It Works

The script constructs a system prompt and user prompt using the provided clinical notes and summary, then evaluates the summary against the full **PDSQI-9** rubric. Outputs are returned in JSON with free-text justifications and scores for each attribute.

### Expected Inputs
- notes: dict[int, str] - a dictionary with note text as string values. Keys are used as identifiers in summary citations
- summary: str - the summary being evaluated. Citations are expected to be in ```<Note ID:int>``` format and correspond to items in the notes input
- target_specialty: str - the target specialty for the summary as a string. For example, "Family Medicine" or "Cardiology"


### Evaluation Attributes

- Citation  
- Accurate  
- Thorough  
- Useful  
- Organized  
- Comprehensible  
- Succinct  
- Synthesized  
- Stigmatizing  

See the full, validated instrument here:  
👉 [PDSQI-9 Rubric Repository](https://git.doit.wisc.edu/smph-public/dom/uw-icu-data-science-lab-public/pdsqi-9)

---

## 📚 Resources

- **NPJ Digital Medicine (2024):**  
  *Current and Future State of Evaluation of Large Language for Medical Summarization Tasks*  
  https://www.nature.com/articles/s44401-024-00011-2

- **arXiv (2024):**  
  *Development and Validation of the Provider Documentation Summarization Quality Instrument for Large Language Models (PDSQI-9)*  
  https://arxiv.org/abs/2501.08977

- **medRxiv (2025):**  
  *Automating Evaluation of AI Text Generation in Healthcare with a Large Language Model (LLM)-as-a-Judge*  
  https://www.medrxiv.org/content/10.1101/2025.04.22.25326219v1

---

## 🔖 Citation

If you use the PDSQI-9 instrument or its integration as an LLM-as-a-Judge for scale and automation, please cite our work:

### For the PDSQI-9 paper:

```bibtex
@article{croxford2025developmentvalidationproviderdocumentation,
      title={Development and Validation of the Provider Documentation Summarization Quality Instrument for Large Language Models}, 
      author={Emma Croxford and Yanjun Gao and Nicholas Pellegrino and Karen K. Wong and Graham Wills and Elliot First and Miranda Schnier and Kyle Burton and Cris G. Ebby and Jillian Gorskic and Matthew Kalscheur and Samy Khalil and Marie Pisani and Tyler Rubeor and Peter Stetson and Frank Liao and Cherodeep Goswami and Brian Patterson and Majid Afshar},
      year={2025},
      eprint={2501.08977},
      archivePrefix={arXiv},
      url={https://arxiv.org/abs/2501.08977}, 
}
```

### For the medical LLM-as-a-Judge paper:

```bibtex
@article {Croxford2025.04.22.25326219,
	author = {Croxford, Emma and Gao, Yanjun and First, Elliot and Pellegrino, Nicholas and Schnier, Miranda and Caskey, John and Oguss, Madeline and Wills, Graham and Chen, Guanhua and Dligach, Dmitriy and Churpek, Matthew M and Mayampurath, Anoop and Liao, Frank and Goswami, Cherodeep and Wong, Karen K. and Patterson, Brian W. and Afshar, Majid},
	title = {Automating Evaluation of AI Text Generation in Healthcare with a Large Language Model (LLM)-as-a-Judge},
	year = {2025},
	publisher = {Cold Spring Harbor Laboratory Press},
	URL = {https://www.medrxiv.org/content/early/2025/04/22/2025.04.22.25326219},
	journal = {medRxiv}
}
```

## 🤝 Acknowledgments

This work was made possible through collaboration between Epic, UW Health, and the University of Wisconsin–Madison School of Medicine and Public Health. 

Special thanks to:

- Clinical reviewers and physician collaborators who validated the PDSQI-9 rubric
- The Epic XGM community for feedback during early implementation
- The UW Data Science Lab for running the experiments
- All contributors who supported open-source development of LLM-as-a-Judge

This project is part of a broader effort to promote safe, scalable, and evidence-based implementation of generative AI in real-world healthcare settings.
