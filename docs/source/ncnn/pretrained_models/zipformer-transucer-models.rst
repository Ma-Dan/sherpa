Zipformer-transducer-based Models
=================================

csukuangfj/sherpa-ncnn-streaming-zipformer-en-2023-02-13 (English)
------------------------------------------------------------------

This model is converted from

`<https://huggingface.co/csukuangfj/sherpa-ncnn-streaming-zipformer-en-2023-02-13>`_

which supports only English as it is trained on the `LibriSpeech`_ corpus.

You can find the training code at

`<https://github.com/k2-fsa/icefall/tree/master/egs/librispeech/ASR/pruned_transducer_stateless7_streaming>`_

In the following, we describe how to download it and use it with `sherpa-ncnn`_.

Download the model
~~~~~~~~~~~~~~~~~~

Please use the following commands to download it.

.. code-block:: bash

  cd /path/to/sherpa-ncnn

  GIT_LFS_SKIP_SMUDGE=1 git clone https://huggingface.co/csukuangfj/sherpa-ncnn-streaming-zipformer-en-2023-02-13

  cd sherpa-ncnn-streaming-zipformer-en-2023-02-13
  git lfs pull --include "*.bin"

Please check that the file sizes of the pre-trained models are correct. See
the file sizes of ``*.bin`` files below.

.. code-block:: bash

  # before running `git lfs pull`

  sherpa-ncnn-streaming-zipformer-en-2023-02-13 fangjun$ ls -lh *.bin

  -rw-r--r--  1 fangjun  staff   131B Feb 14 11:51 decoder_jit_trace-pnnx.ncnn.bin
  -rw-r--r--  1 fangjun  staff   134B Feb 14 11:51 encoder_jit_trace-pnnx.ncnn.bin
  -rw-r--r--  1 fangjun  staff   132B Feb 14 11:51 joiner_jit_trace-pnnx.ncnn.bin

  sherpa-ncnn-streaming-zipformer-en-2023-02-13 fangjun$ git lfs pull --include "*.bin"

  # after running `git lfs pull`

  sherpa-ncnn-streaming-zipformer-en-2023-02-13 fangjun$ ls -lh *.bin

  -rw-r--r--  1 fangjun  staff   508K Feb 14 22:19 decoder_jit_trace-pnnx.ncnn.bin
  -rw-r--r--  1 fangjun  staff   132M Feb 14 22:19 encoder_jit_trace-pnnx.ncnn.bin
  -rw-r--r--  1 fangjun  staff   1.4M Feb 14 22:19 joiner_jit_trace-pnnx.ncnn.bin

Decode a single wave file
~~~~~~~~~~~~~~~~~~~~~~~~~

.. hint::

   It supports decoding only wave files with a single channel and the sampling rate
   should be 16 kHz.

.. code-block:: bash

  cd /path/to/sherpa-ncnn

  for method in greedy_search modified_beam_search; do
    ./build/bin/sherpa-ncnn \
      ./sherpa-ncnn-streaming-zipformer-en-2023-02-13/tokens.txt \
      ./sherpa-ncnn-streaming-zipformer-en-2023-02-13/encoder_jit_trace-pnnx.ncnn.param \
      ./sherpa-ncnn-streaming-zipformer-en-2023-02-13/encoder_jit_trace-pnnx.ncnn.bin \
      ./sherpa-ncnn-streaming-zipformer-en-2023-02-13/decoder_jit_trace-pnnx.ncnn.param \
      ./sherpa-ncnn-streaming-zipformer-en-2023-02-13/decoder_jit_trace-pnnx.ncnn.bin \
      ./sherpa-ncnn-streaming-zipformer-en-2023-02-13/joiner_jit_trace-pnnx.ncnn.param \
      ./sherpa-ncnn-streaming-zipformer-en-2023-02-13/joiner_jit_trace-pnnx.ncnn.bin \
      ./sherpa-ncnn-streaming-zipformer-en-2023-02-13/test_wavs/1221-135766-0002.wav \
      2 \
      $method
  done

You should see the following output:

.. literalinclude:: ./code-zipformer/sherpa-ncnn-streaming-zipformer-en-2023-02-13-sherpa-ncnn.txt

.. note::

   Please use ``./build/bin/Release/sherpa-ncnn.exe`` for Windows.

Real-time speech recognition from a microphone
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

  cd /path/to/sherpa-ncnn

  ./build/bin/sherpa-ncnn-microphone \
    ./sherpa-ncnn-streaming-zipformer-en-2023-02-13/tokens.txt \
    ./sherpa-ncnn-streaming-zipformer-en-2023-02-13/encoder_jit_trace-pnnx.ncnn.param \
    ./sherpa-ncnn-streaming-zipformer-en-2023-02-13/encoder_jit_trace-pnnx.ncnn.bin \
    ./sherpa-ncnn-streaming-zipformer-en-2023-02-13/decoder_jit_trace-pnnx.ncnn.param \
    ./sherpa-ncnn-streaming-zipformer-en-2023-02-13/decoder_jit_trace-pnnx.ncnn.bin \
    ./sherpa-ncnn-streaming-zipformer-en-2023-02-13/joiner_jit_trace-pnnx.ncnn.param \
    ./sherpa-ncnn-streaming-zipformer-en-2023-02-13/joiner_jit_trace-pnnx.ncnn.bin \
    2 \
    greedy_search

.. _sherpa_ncnn_streaming_zipformer_bilingual_zh_en_2023_02_13:

csukuangfj/sherpa-ncnn-streaming-zipformer-bilingual-zh-en-2023-02-13 (Bilingual, Chinese + English)
----------------------------------------------------------------------------------------------------

This model is converted from

`<https://huggingface.co/pfluo/k2fsa-zipformer-chinese-english-mixed>`_

which supports both Chinese and English. The model is contributed by the community
and is trained on tens of thousands of some internal dataset.

In the following, we describe how to download it and use it with `sherpa-ncnn`_.

Download the model
~~~~~~~~~~~~~~~~~~

Please use the following commands to download it.

.. code-block:: bash

  cd /path/to/sherpa-ncnn

  GIT_LFS_SKIP_SMUDGE=1 git clone https://huggingface.co/csukuangfj/sherpa-ncnn-streaming-zipformer-bilingual-zh-en-2023-02-13
  cd sherpa-ncnn-streaming-zipformer-bilingual-zh-en-2023-02-13
  git lfs pull --include "*.bin"

Please check that the file sizes of the pre-trained models are correct. See
the file sizes of ``*.bin`` files below.

.. code-block:: bash

  sherpa-ncnn-streaming-zipformer-bilingual-zh-en-2023-02-13 fangjun$ ls -lh *.bin

  -rw-r--r--  1 fangjun  staff   6.1M Feb 14 10:08 decoder_jit_trace-pnnx.ncnn.bin
  -rw-r--r--  1 fangjun  staff   121M Feb 14 10:09 encoder_jit_trace-pnnx.ncnn.bin
  -rw-r--r--  1 fangjun  staff   7.0M Feb 14 10:08 joiner_jit_trace-pnnx.ncnn.bin

Decode a single wave file
~~~~~~~~~~~~~~~~~~~~~~~~~

.. hint::

   It supports decoding only wave files with a single channel and the sampling rate
   should be 16 kHz.

.. code-block:: bash

  cd /path/to/sherpa-ncnn

  for method in greedy_search modified_beam_search; do
    ./build/bin/sherpa-ncnn \
      ./sherpa-ncnn-streaming-zipformer-bilingual-zh-en-2023-02-13/tokens.txt \
      ./sherpa-ncnn-streaming-zipformer-bilingual-zh-en-2023-02-13/encoder_jit_trace-pnnx.ncnn.param \
      ./sherpa-ncnn-streaming-zipformer-bilingual-zh-en-2023-02-13/encoder_jit_trace-pnnx.ncnn.bin \
      ./sherpa-ncnn-streaming-zipformer-bilingual-zh-en-2023-02-13/decoder_jit_trace-pnnx.ncnn.param \
      ./sherpa-ncnn-streaming-zipformer-bilingual-zh-en-2023-02-13/decoder_jit_trace-pnnx.ncnn.bin \
      ./sherpa-ncnn-streaming-zipformer-bilingual-zh-en-2023-02-13/joiner_jit_trace-pnnx.ncnn.param \
      ./sherpa-ncnn-streaming-zipformer-bilingual-zh-en-2023-02-13/joiner_jit_trace-pnnx.ncnn.bin \
      ./sherpa-ncnn-streaming-zipformer-bilingual-zh-en-2023-02-13/test_wavs/1.wav \
      2 \
      $method
  done

You should see the following output:

.. literalinclude:: ./code-zipformer/sherpa-ncnn-streaming-zipformer-bilingual-zh-en-2023-02-13-sherpa-ncnn.txt

.. note::

   Please use ``./build/bin/Release/sherpa-ncnn.exe`` for Windows.

.. caution::

   If you use Windows and get encoding issues, please run:

      .. code-block:: bash

          CHCP 65001

   in your commandline.

Real-time speech recognition from a microphone
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

  cd /path/to/sherpa-ncnn

  ./build/bin/sherpa-ncnn-microphone \
    ./sherpa-ncnn-streaming-zipformer-bilingual-zh-en-2023-02-13/tokens.txt \
    ./sherpa-ncnn-streaming-zipformer-bilingual-zh-en-2023-02-13/encoder_jit_trace-pnnx.ncnn.param \
    ./sherpa-ncnn-streaming-zipformer-bilingual-zh-en-2023-02-13/encoder_jit_trace-pnnx.ncnn.bin \
    ./sherpa-ncnn-streaming-zipformer-bilingual-zh-en-2023-02-13/decoder_jit_trace-pnnx.ncnn.param \
    ./sherpa-ncnn-streaming-zipformer-bilingual-zh-en-2023-02-13/decoder_jit_trace-pnnx.ncnn.bin \
    ./sherpa-ncnn-streaming-zipformer-bilingual-zh-en-2023-02-13/joiner_jit_trace-pnnx.ncnn.param \
    ./sherpa-ncnn-streaming-zipformer-bilingual-zh-en-2023-02-13/joiner_jit_trace-pnnx.ncnn.bin \
    2 \
    greedy_search


.. _sherpa_ncnn_streaming_zipformer_small_bilingual_zh_en_2023_02_16:

csukuangfj/sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16 (Bilingual, Chinese + English)
----------------------------------------------------------------------------------------------------------

This model is converted from

`<https://huggingface.co/pfluo/k2fsa-zipformer-bilingual-zh-en-t>`_

which supports both Chinese and English. The model is contributed by the community
and is trained on tens of thousands of some internal dataset.

In the following, we describe how to download it and use it with `sherpa-ncnn`_.

.. note::

  Unlinke :ref:`sherpa_ncnn_streaming_zipformer_bilingual_zh_en_2023_02_13`, this
  model is much smaller.

Download the model
~~~~~~~~~~~~~~~~~~


Please use the following commands to download it.

.. code-block:: bash

  cd /path/to/sherpa-ncnn

  GIT_LFS_SKIP_SMUDGE=1 git clone https://huggingface.co/csukuangfj/sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16
  cd sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16
  git lfs pull --include "*.bin"


Please check that the file sizes of the pre-trained models are correct. See
the file sizes of ``*.bin`` files below.

.. code-block:: bash

  # before running `git lfs pull`

  sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16 fangjun$ ls -lh *.bin
  -rw-r--r--  1 fangjun  staff   132B Feb 16 12:18 decoder_jit_trace-pnnx.ncnn.bin
  -rw-r--r--  1 fangjun  staff   133B Feb 16 12:18 encoder_jit_trace-pnnx.ncnn.bin
  -rw-r--r--  1 fangjun  staff   132B Feb 16 12:18 joiner_jit_trace-pnnx.ncnn.bin

  sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16 fangjun$ git lfs pull --include "*.bin"

  # after running `git lfs pull`

  sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16 fangjun$ ls -lh *.bin
  -rw-r--r--  1 fangjun  staff   6.1M Feb 16 12:18 decoder_jit_trace-pnnx.ncnn.bin
  -rw-r--r--  1 fangjun  staff    37M Feb 16 12:19 encoder_jit_trace-pnnx.ncnn.bin
  -rw-r--r--  1 fangjun  staff   6.9M Feb 16 12:18 joiner_jit_trace-pnnx.ncnn.bin

Decode a single wave file
~~~~~~~~~~~~~~~~~~~~~~~~~

.. hint::

   It supports decoding only wave files with a single channel and the sampling rate
   should be 16 kHz.

.. code-block:: bash

  cd /path/to/sherpa-ncnn

  for method in greedy_search modified_beam_search; do
    ./build/bin/sherpa-ncnn \
      ./sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/tokens.txt \
      ./sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/encoder_jit_trace-pnnx.ncnn.param \
      ./sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/encoder_jit_trace-pnnx.ncnn.bin \
      ./sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/decoder_jit_trace-pnnx.ncnn.param \
      ./sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/decoder_jit_trace-pnnx.ncnn.bin \
      ./sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/joiner_jit_trace-pnnx.ncnn.param \
      ./sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/joiner_jit_trace-pnnx.ncnn.bin \
      ./sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/test_wavs/1.wav \
      2 \
      $method
  done

You should see the following output:

.. literalinclude:: ./code-zipformer/sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16.txt

.. note::

   Please use ``./build/bin/Release/sherpa-ncnn.exe`` for Windows.

Real-time speech recognition from a microphone
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

  cd /path/to/sherpa-ncnn

  ./build/bin/sherpa-ncnn-microphone \
    ./sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/tokens.txt \
    ./sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/encoder_jit_trace-pnnx.ncnn.param \
    ./sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/encoder_jit_trace-pnnx.ncnn.bin \
    ./sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/decoder_jit_trace-pnnx.ncnn.param \
    ./sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/decoder_jit_trace-pnnx.ncnn.bin \
    ./sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/joiner_jit_trace-pnnx.ncnn.param \
    ./sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/joiner_jit_trace-pnnx.ncnn.bin \
    2 \
    greedy_search

A faster model of sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

We provide a second version of the model that is exported with
``--decode-chunk-len=96`` instead of ``32``.

.. hint::

  Please see the model export script at

  `<https://huggingface.co/csukuangfj/sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/blob/main/96/export-for-ncnn-bilingual-small.sh>`_

  if you are interested.


The advantage of using this model is that it runs much faster, while the downside
is that you will see some delay before you see the recognition result after you speak.

In the following, we describe how to download it.

.. code-block:: bash

  cd sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16
  cd 96/
  git lfs pull --include "*.bin"

After downloading, please check the file sizes of ``*.bin`` files:

.. code-block:: bash

  sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16 fangjun$ ls -lh 96/*.bin

  -rw-r--r--  1 fangjun  staff   6.1M Feb 16 14:39 96/decoder_jit_trace-pnnx.ncnn.bin
  -rw-r--r--  1 fangjun  staff    38M Feb 16 14:39 96/encoder_jit_trace-pnnx.ncnn.bin
  -rw-r--r--  1 fangjun  staff   6.9M Feb 16 14:39 96/joiner_jit_trace-pnnx.ncnn.bin


To decode a file, please use:

.. code-block:: bash

  cd /path/to/sherpa-ncnn

  for method in greedy_search modified_beam_search; do
    ./build/bin/sherpa-ncnn \
      ./sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/96/tokens.txt \
      ./sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/96/encoder_jit_trace-pnnx.ncnn.param \
      ./sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/96/encoder_jit_trace-pnnx.ncnn.bin \
      ./sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/96/decoder_jit_trace-pnnx.ncnn.param \
      ./sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/96/decoder_jit_trace-pnnx.ncnn.bin \
      ./sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/96/joiner_jit_trace-pnnx.ncnn.param \
      ./sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/96/joiner_jit_trace-pnnx.ncnn.bin \
      ./sherpa-ncnn-streaming-zipformer-small-bilingual-zh-en-2023-02-16/test_wavs/1.wav \
      2 \
      $method
  done


csukuangfj/sherpa-ncnn-streaming-zipformer-ja-fluent-2023-02-14 (Japanese)
--------------------------------------------------------------------------

This model is converted from

`<https://huggingface.co/TeoWenShen/icefall-asr-csj-pruned-transducer-stateless7-streaming-230208/tree/main/exp_fluent>`_

which supports only Japanese as it is trained on the `CSJ`_ corpus.

You can find the training code at

`<https://github.com/k2-fsa/icefall/tree/master/egs/csj/ASR/pruned_transducer_stateless7_streaming>`_

In the following, we describe how to download it and use it with `sherpa-ncnn`_.

Download the model
~~~~~~~~~~~~~~~~~~

Please use the following commands to download it.

.. code-block:: bash

  cd /path/to/sherpa-ncnn

  GIT_LFS_SKIP_SMUDGE=1 git clone https://huggingface.co/csukuangfj/sherpa-ncnn-streaming-zipformer-ja-fluent-2023-02-14
  cd sherpa-ncnn-streaming-zipformer-ja-fluent-2023-02-14
  git lfs pull --include "*.bin"
  git lfs pull --include "test_wavs/*.wav"

Please check that the file sizes of the pre-trained models are correct. See
the file sizes of ``*.bin`` files below.

.. code-block:: bash

  # before running `git lfs pull`

  sherpa-ncnn-streaming-zipformer-ja-fluent-2023-02-14 fangjun$ ls -lh *.bin
  -rw-r--r--  1 fangjun  staff   132B Feb 14 22:19 decoder_jit_trace-pnnx.ncnn.bin
  -rw-r--r--  1 fangjun  staff   134B Feb 14 22:19 encoder_jit_trace-pnnx.ncnn.bin
  -rw-r--r--  1 fangjun  staff   132B Feb 14 22:19 joiner_jit_trace-pnnx.ncnn.bin

  sherpa-ncnn-streaming-zipformer-ja-fluent-2023-02-14 fangjun$ git lfs pull --include "*.bin"

  # after running `git lfs pull`

  sherpa-ncnn-streaming-zipformer-ja-fluent-2023-02-14 fangjun$ ls -lh *.bin
  -rw-r--r--  1 fangjun  staff   3.2M Feb 15 11:08 decoder_jit_trace-pnnx.ncnn.bin
  -rw-r--r--  1 fangjun  staff   132M Feb 15 11:09 encoder_jit_trace-pnnx.ncnn.bin
  -rw-r--r--  1 fangjun  staff   4.1M Feb 15 11:08 joiner_jit_trace-pnnx.ncnn.bin

Decode a single wave file
~~~~~~~~~~~~~~~~~~~~~~~~~

.. hint::

   It supports decoding only wave files with a single channel and the sampling rate
   should be 16 kHz.

.. code-block:: bash

  cd /path/to/sherpa-ncnn

  for method in greedy_search modified_beam_search; do
    ./build/bin/sherpa-ncnn \
      ./sherpa-ncnn-streaming-zipformer-ja-fluent-2023-02-14/tokens.txt \
      ./sherpa-ncnn-streaming-zipformer-ja-fluent-2023-02-14/encoder_jit_trace-pnnx.ncnn.param \
      ./sherpa-ncnn-streaming-zipformer-ja-fluent-2023-02-14/encoder_jit_trace-pnnx.ncnn.bin \
      ./sherpa-ncnn-streaming-zipformer-ja-fluent-2023-02-14/decoder_jit_trace-pnnx.ncnn.param \
      ./sherpa-ncnn-streaming-zipformer-ja-fluent-2023-02-14/decoder_jit_trace-pnnx.ncnn.bin \
      ./sherpa-ncnn-streaming-zipformer-ja-fluent-2023-02-14/joiner_jit_trace-pnnx.ncnn.param \
      ./sherpa-ncnn-streaming-zipformer-ja-fluent-2023-02-14/joiner_jit_trace-pnnx.ncnn.bin \
      ./sherpa-ncnn-streaming-zipformer-ja-fluent-2023-02-14/test_wavs/aps-smp.wav \
      2 \
      $method
  done

You should see the following output:

.. literalinclude:: ./code-zipformer/sherpa-ncnn-streaming-zipformer-ja-fluent-2023-02-14.txt

.. note::

   Please use ``./build/bin/Release/sherpa-ncnn.exe`` for Windows.

.. caution::

   If you use Windows and get encoding issues, please run:

      .. code-block:: bash

          CHCP 65001

   in your commandline.

Real-time speech recognition from a microphone
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

  cd /path/to/sherpa-ncnn

  ./build/bin/sherpa-ncnn-microphone \
    ./sherpa-ncnn-streaming-zipformer-ja-fluent-2023-02-14/tokens.txt \
    ./sherpa-ncnn-streaming-zipformer-ja-fluent-2023-02-14/encoder_jit_trace-pnnx.ncnn.param \
    ./sherpa-ncnn-streaming-zipformer-ja-fluent-2023-02-14/encoder_jit_trace-pnnx.ncnn.bin \
    ./sherpa-ncnn-streaming-zipformer-ja-fluent-2023-02-14/decoder_jit_trace-pnnx.ncnn.param \
    ./sherpa-ncnn-streaming-zipformer-ja-fluent-2023-02-14/decoder_jit_trace-pnnx.ncnn.bin \
    ./sherpa-ncnn-streaming-zipformer-ja-fluent-2023-02-14/joiner_jit_trace-pnnx.ncnn.param \
    ./sherpa-ncnn-streaming-zipformer-ja-fluent-2023-02-14/joiner_jit_trace-pnnx.ncnn.bin \
    2 \
    greedy_search


csukuangfj/sherpa-ncnn-streaming-zipformer-ja-disfluent-2023-02-14 (Japanese)
-----------------------------------------------------------------------------


This model is converted from

`<https://huggingface.co/TeoWenShen/icefall-asr-csj-pruned-transducer-stateless7-streaming-230208/tree/main/exp_disfluent>`_

which supports only Japanese as it is trained on the `CSJ`_ corpus.

You can find the training code at

`<https://github.com/k2-fsa/icefall/tree/master/egs/csj/ASR/pruned_transducer_stateless7_streaming>`_

In the following, we describe how to download it and use it with `sherpa-ncnn`_.

Download the model
~~~~~~~~~~~~~~~~~~

Please use the following commands to download it.

.. code-block:: bash

  cd /path/to/sherpa-ncnn

  GIT_LFS_SKIP_SMUDGE=1 git clone https://huggingface.co/csukuangfj/sherpa-ncnn-streaming-zipformer-ja-disfluent-2023-02-14
  cd sherpa-ncnn-streaming-zipformer-ja-disfluent-2023-02-14
  git lfs pull --include "*.bin"
  git lfs pull --include "test_wavs/*.wav"

Please check that the file sizes of the pre-trained models are correct. See
the file sizes of ``*.bin`` files below.

.. code-block:: bash

  # before running `git lfs pull`

  sherpa-ncnn-streaming-zipformer-ja-disfluent-2023-02-14 fangjun$ ls -lh *.bin

  -rw-r--r--  1 fangjun  staff   132B Feb 14 22:20 decoder_jit_trace-pnnx.ncnn.bin
  -rw-r--r--  1 fangjun  staff   134B Feb 14 22:20 encoder_jit_trace-pnnx.ncnn.bin
  -rw-r--r--  1 fangjun  staff   132B Feb 14 22:20 joiner_jit_trace-pnnx.ncnn.bin

  sherpa-ncnn-streaming-zipformer-ja-disfluent-2023-02-14 fangjun$ git lfs pull --include "*.bin"

  # after running `git lfs pull`

  sherpa-ncnn-streaming-zipformer-ja-disfluent-2023-02-14 fangjun$ ls -lh *.bin

  -rw-r--r--  1 fangjun  staff   3.2M Feb 15 14:50 decoder_jit_trace-pnnx.ncnn.bin
  -rw-r--r--  1 fangjun  staff   132M Feb 15 14:51 encoder_jit_trace-pnnx.ncnn.bin
  -rw-r--r--  1 fangjun  staff   4.1M Feb 15 14:50 joiner_jit_trace-pnnx.ncnn.bin

Decode a single wave file
~~~~~~~~~~~~~~~~~~~~~~~~~

.. hint::

   It supports decoding only wave files with a single channel and the sampling rate
   should be 16 kHz.

.. code-block:: bash

  cd /path/to/sherpa-ncnn

  for method in greedy_search modified_beam_search; do
    ./build/bin/sherpa-ncnn \
      ./sherpa-ncnn-streaming-zipformer-ja-disfluent-2023-02-14/tokens.txt \
      ./sherpa-ncnn-streaming-zipformer-ja-disfluent-2023-02-14/encoder_jit_trace-pnnx.ncnn.param \
      ./sherpa-ncnn-streaming-zipformer-ja-disfluent-2023-02-14/encoder_jit_trace-pnnx.ncnn.bin \
      ./sherpa-ncnn-streaming-zipformer-ja-disfluent-2023-02-14/decoder_jit_trace-pnnx.ncnn.param \
      ./sherpa-ncnn-streaming-zipformer-ja-disfluent-2023-02-14/decoder_jit_trace-pnnx.ncnn.bin \
      ./sherpa-ncnn-streaming-zipformer-ja-disfluent-2023-02-14/joiner_jit_trace-pnnx.ncnn.param \
      ./sherpa-ncnn-streaming-zipformer-ja-disfluent-2023-02-14/joiner_jit_trace-pnnx.ncnn.bin \
      ./sherpa-ncnn-streaming-zipformer-ja-disfluent-2023-02-14/test_wavs/interview_aps-smp.wav \
      2 \
      $method
  done

You should see the following output:

.. literalinclude:: ./code-zipformer/sherpa-ncnn-streaming-zipformer-ja-disfluent-2023-02-14.txt

.. note::

   Please use ``./build/bin/Release/sherpa-ncnn.exe`` for Windows.

.. caution::

   If you use Windows and get encoding issues, please run:

      .. code-block:: bash

          CHCP 65001

   in your commandline.

Real-time speech recognition from a microphone
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

  cd /path/to/sherpa-ncnn

  ./build/bin/sherpa-ncnn-microphone \
    ./sherpa-ncnn-streaming-zipformer-ja-disfluent-2023-02-14/tokens.txt \
    ./sherpa-ncnn-streaming-zipformer-ja-disfluent-2023-02-14/encoder_jit_trace-pnnx.ncnn.param \
    ./sherpa-ncnn-streaming-zipformer-ja-disfluent-2023-02-14/encoder_jit_trace-pnnx.ncnn.bin \
    ./sherpa-ncnn-streaming-zipformer-ja-disfluent-2023-02-14/decoder_jit_trace-pnnx.ncnn.param \
    ./sherpa-ncnn-streaming-zipformer-ja-disfluent-2023-02-14/decoder_jit_trace-pnnx.ncnn.bin \
    ./sherpa-ncnn-streaming-zipformer-ja-disfluent-2023-02-14/joiner_jit_trace-pnnx.ncnn.param \
    ./sherpa-ncnn-streaming-zipformer-ja-disfluent-2023-02-14/joiner_jit_trace-pnnx.ncnn.bin \
    2 \
    greedy_search