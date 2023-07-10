FROM tensorflow/tensorflow:2.8.0-gpu
RUN rm /bin/sh && ln -s /bin/bash /bin/sh

RUN pip install jupyterlab

WORKDIR /home
COPY ./requirements.txt .
RUN pip install -r requirements.txt

COPY ./U-Net_2D_Multilabel_ZeroCostDL4Mic.ipynb .

CMD [ "jupyter-lab", "U-Net_2D_Multilabel_ZeroCostDL4Mic.ipynb", "--ip='0.0.0.0'", "--port=8888", "--no-browser", "--allow-root" ]