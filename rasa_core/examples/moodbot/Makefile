help:
	@echo "    train-nlu"
	@echo "        Train the natural language understanding using Rasa NLU."
	@echo "    train-core"
	@echo "        Train a dialogue model using Rasa core."
	@echo "    run-{channel}"
	@echo "        Spin up a server that uses the connector for {channel}."
	@echo "    evaluate-nlu"
	@echo "        Evaluates the nlu data."
	@echo "    visualize"
	@echo "        Show your stories as a graph."

train-nlu:
	python -m rasa_nlu.train -c nlu_model_config.yml --fixed_model_name current \
	       --data ./data/nlu.md --path models/ --project nlu

train-core:
	python -m rasa_core.train -s data/stories.md -d domain.yml -o models/dialogue

run-fb:
	python -m rasa_core.run -d models/dialogue -u models/nlu/current -p 5002 -c facebook --credentials credentials.yml

run-slack:
	python -m rasa_core.run -d models/dialogue -u models/nlu/current -p 5002 -c slack --credentials credentials.yml

run-telegram:
	python -m rasa_core.run -d models/dialogue -u models/nlu/current -p 5002 -c telegram --credentials credentials.yml

run-rocketchat:
	python -m rasa_core.run -d models/dialogue -u models/nlu/current -p 5002 -c rocketchat --credentials rocketchat_credentials.yml

run-mattermost:
	python -m rasa_core.run -d models/dialogue -u models/nlu/current -p 5002 -c mattermost --credentials credentials.yml

run-twilio:
	python -m rasa_core.run -d models/dialogue -u models/nlu/current -p 5002 -c twilio --credentials credentials.yml

run-webexteams:
	python -m rasa_core.run -d models/dialogue -u models/nlu/current -p 5002 -c webexteams --credentials credentials.yml

run-cmdline:
	python -m rasa_core.run -d models/dialogue -u models/nlu/current

evaluate-nlu:
	python -m rasa_nlu.evaluate  --model models/nlu/current --data ./data/nlu.md

visualize:
	python -m rasa_core.visualize -s data/stories.md -d domain.yml -o story_graph.html
