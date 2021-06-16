FROM python:3.5.9

COPY ./snowflake_modules/requirements.txt /snowflake_modules/requirements.txt

RUN cd /snowflake_modules && cp -rp requirements.txt ../requirements.txt

RUN pip install -r requirements.txt