.. _Adding Models:

Adding Models
=============

.. contents:: Table of Contents
    :depth: 3
    :local:

.. _adding-models-overview:

Overview
--------

The :doc:`Model Prebuilts page </prebuilt_models>` records all the model variants you can use off-the-shelf. However, what if the model you would like is not supported? Besides, what if you would want to contribute to the existing range of model prebuilts?

This page documents:

- Requesting a model
- Adding support for a model

.. _requesting-model:

Requesting a model
------------------

To request a model, you can simply `submit an issue <https://github.com/mlc-ai/mlc-llm/issues/new?assignees=&labels=new-models&projects=&template=model-request.md&title=%5BModel+Request%5D+>`__ in Github with the label ``new-models`` (``[Model Request]`` in title). Your request will then pop up in the `model request tracking dashboard <https://github.com/orgs/mlc-ai/projects/2>`__.


.. _adding-support:

Adding support for a model
--------------------------

There are generally three cases for adding support for a model:

1. The model variant is already supported, and you are complementing a new :ref:`model library file <model-library-tables>`, or :ref:`new compiled weights <model-variant-tables>`.
2. The model is a new variant with an already supported architecture (e.g. adding support for :ref:`WizardMath <wizard_math_variant_table>`)
3. The model uses an architecture not supported (i.e. does not appear in the :ref:`supported model architectures table <supported-model-architectures>`)


1. Complement to an existing model variant
------------------------------------------

This section applies to when the :ref:`model variant table <model-variant-tables>` or the :ref:`model library table <model-library-tables>` you are looking at does not have an entry for the configuration you would like (e.g. platform, quantization scheme, etc.).

First, you can follow the :doc:`tutorial on compiling models </compilation/compile_models>` (or its :doc:`Python version </compilation/python>`). 

Afterwards, to share your new model library binary file, you may submit a PR to `this Github repo <https://github.com/mlc-ai/binary-mlc-llm-libs>`__.

To share your newly compiled weights, first :doc:`distribute the weights </compilation/distribute_compiled_models>` to hugging face, then you could either submit a PR to modify the corresponding :ref:`model variant table <model-variant-tables>`, or simply add an entry to the `contribution log <https://github.com/CharlieFRuan/mlc-llm/tree/pr-docs-contribution-log/docs/_contribution_log>`__ so that we can update the documentation for you.


2. Add a new model variant
--------------------------

To add a new model variant, you would only need to compile a new set of weights, since you may reuse the model library file that shares the same architecture.

The steps would be similar to the previous section, and this `python tutorial notebook <https://github.com/mlc-ai/notebooks/blob/main/mlc-llm/tutorial_extensions_to_more_model_variants.ipynb>`__ (runnable on Google Colab) may be particularly helpful, where we run through the process of compiling an unsupported model variant (with ``llama`` architecture in this case).

While the steps are almost identical to the previous section, you may need to pay extra attention to the part of tuning conversation template, since each model, despite sharing the architecture, may have different formats when prompting or generating texts.

You may need to submit a PR to add a conversation template to `conv_templates.cc <https://github.com/mlc-ai/mlc-llm/blob/main/cpp/conv_templates.cc>`__. Here are some examples: `WizardLM's conversation template PR <https://github.com/mlc-ai/mlc-llm/pull/489/files>`__, `Gorilla's conversation template PR <https://github.com/mlc-ai/mlc-llm/pull/288>`__.

For more details on conversation template, please refer to the page :doc:`Configure MLCChat in JSON </get_started/mlc_chat_config>`.

When you finish, similar to the previous section, first :doc:`distribute the weights </compilation/distribute_compiled_models>` to hugging face, then you could either submit a PR to modify the corresponding :ref:`model variant table <model-variant-tables>`, or simply add an entry to the `contribution log <https://github.com/CharlieFRuan/mlc-llm/tree/pr-docs-contribution-log/docs/_contribution_log>`__ so that we can update the documentation for you.


3. Add support to a new model architecture
------------------------------------------

If your model's architecture is not included in the :ref:`supported model architectures table <supported-model-architectures>`, you may want to either :ref:`submit a request <requesting-model>`, or follow the steps below.


Step 1: Define new model architecture in relax
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Since the model architecture is not supported, it is required to implement the model in Relax. The :doc:`Define New Model Architectures </tutorials/customize/define_new_models>` page teaches the high-level knowledge of using Relax to define a model. Each file under the `relax_model folder <https://github.com/mlc-ai/mlc-llm/tree/main/mlc_llm/relax_model>`__ correspond to an architecture (as linked in the :ref:`model architectures table <supported-model-architectures>`), and you would need to implement another such file for your model. Afterwards, submit a PR to include the newly added file.

Step 2: Check conversation template support
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

After implementing the architecture, the rest of the steps are identical to the previous section. 

We first check whether an existing conversation template supports the model variant you are adding. If not, submit a PR to define a new template.

Step 3: Compile and Distribute
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Finally, you may distribute the model library and weights you have compiled so that others can use it right off-the-shelf!

Again, to share a compiled model library, submit a PR to `this Github repo <https://github.com/mlc-ai/binary-mlc-llm-libs>`__. To share compiled weights, you could either submit a PR to modify the corresponding :ref:`model variant table <model-variant-tables>`, or simply add an entry to the `contribution log <https://github.com/CharlieFRuan/mlc-llm/tree/pr-docs-contribution-log/docs/_contribution_log>`__ so that we can update the documentation for you.