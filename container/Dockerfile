FROM python:3.8-slim
MAINTAINER David Soichi Nakahashi <sdn03.tech@gmail.com>

# Setup python packeges
COPY ./Pipfile Pipfile
COPY ./Pipfile.lock Pipfile.lock
RUN pip3 install pipenv
RUN pipenv install --system

# Configuring access to Jupyter
RUN mkdir /opt/notebooks
RUN jupyter notebook --generate-config --allow-root
RUN echo "c.NotebookApp.password = u'sha1:6a3f528eec40:6e896b6e4828f525a6e20e5411cd1c8075d68619'" >> /root/.jupyter/jupyter_notebook_config.py

# Jupyter listens port: 8888
EXPOSE 8888

# Run Jupyter notebook as Docker main process
CMD ["jupyter", "notebook", "--allow-root", "--notebook-dir=/opt/notebooks", "--ip='*'", "--port=8888", "--no-browser"]
