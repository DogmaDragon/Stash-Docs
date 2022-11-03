---
layout: default
title: JSON Specification
nav_order: 13
---
# **JSON Specification**
<details open markdown="block">
  <summary>
    Table of Contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

# Introduction

The Metadata given to Stash can be exported into the JSON format. This structure can be modified, or replicated by other means. The resulting data can then be imported again, giving the possibility for automatic scraping of all kinds. The format of this Metadata bulk is a folder Structure, containing the folders 
  
downloads, galleries, performers, scenes, studios  
  
as well as a file called  
  
mappings.json
  
The mappings file contains a reference to all files within the folders, by including their checksum. All files in the aforementioned folders are named by their checksum (like 967ddf2e028f10fc8d36901833c25732.json), which (at least in the case of galleries and scenes) is generated from the file that this metadata relates to. The algorithm for the checksum is MD5. 

# Content of the jsons

In the following, the values of the according jsons will be shown. If the value should be a number, it is written with after comma values (like 29.98 or 50.0), but still as a string. the The meaning from most of them should be obvious due to the previous explanation or from the possible values stash offers when editing, otherwise a short comment will be added.  
The json values are given as strings, if not stated otherwise. Every new line will stand for a new value in the json. If the value is a list of objects, the values of that object will be shown indented.  
Talking about the performer.json and the later ones is referring to a singular json contained within the directory the name is referring to, named by the checksum which is given from the mappings.json.  
If a value is empty in any but the mappings.json file, it can be left out of the file entirely. In the mappings.json however, all values must be present, if there are no objects of a type (for example, no performers), the value is simply null.  
Many files have an created_at and updated_at, both are kept in the following format:  
YYYY-MM-DDThh:mm:ssTZD  
example:  
"created_at": "2019-05-03T21:36:58+01:00"

## mappings.json

performers  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;checksum  
studios  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;checksum  
galleries  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;path   
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;checksum  
scenes  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;path   
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;checksum  

## performer.json

name  
url  
twitter  
instagram  
birthdate  
ethnicity  
country  
eye_color  
height  
measurements  
fake_tits  
career_length  
tattoos  
piercings  
image (base64 encoding of the image file)  
created_at  
updated_at  

## studio.json

name  
url  
image (base64 encoding of the image file)  
created_at  
updated_at  

## scene.json
title  
studio  
url  
date  
rating (integer)  
details  
performers (list of strings, performers name)  
tags (list of strings)  
markers     
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;title  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;seconds  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;primary_tag  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;tags (list of strings)  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;created_at  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;updated_at  
file (not a list, but a single object)  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;size (in bytes, no after comma values)  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;duration (in seconds)  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;video_codec (example value: h264)  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;audio_codec (example value: aac)  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;width (integer, in pixel)  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;height (integer, in pixel)  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;framerate  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;bitrate (integer, in Bit)  
created_at  
updated_at  

## gallery.json  

No files of this kind are generated yet.


# Again, in json-format

For those preferring the json-format, defined [here](https://json-schema.org/), the following format may be more interesting:

## mappings.json

```json
{
	"$schema": "http://json-schema.org/draft-07/schema#",
	"$id": "https://github.com/stashapp/stash/wiki/JSON-Specification/mappings.json",
	"title": "mappings",
	"description": "The base file for the metadata. Referring to all other files with names, as well as providing the path to files.",
	"type": "object",
	"properties": {
		"performers": {
			"description": "Link to the performers files along with names",
			"type": "array",
			"items": {
				"type": "object",
				"properties": {
					"name": {
						"type": "string"
					},
					"checksum": {
						"type": "string"
					}
				},
				"required": ["name", "checksum"]
			},
			"minItems": 0,
			"uniqueItems": true
		},
		"studios": {
			"description": "Link to the studio files along with names",
			"type": "array",
			"items": {
				"type": "object",
				"properties": {
					"name": {
						"type": "string"
					},
					"checksum": {
						"type": "string"
					}
				},
				"required": ["name", "checksum"]
			},
			"minItems": 0,
			"uniqueItems": true
		},
		"galleries": {
			"description": "Link to the gallery files along with the path to the content",
			"type": "array",
			"items": {
				"type": "object",
				"properties": {
					"path": {
						"type": "string"
					},
					"checksum": {
						"type": "string"
					}
				},
				"required": ["path", "checksum"]
			},
			"minItems": 0,
			"uniqueItems": true
		},
		"scenes": {
			"description": "Link to the scene files along with the path to the content",
			"type": "array",
			"items": {
				"type": "object",
				"properties": {
					"path": {
						"type": "string"
					},
					"checksum": {
						"type": "string"
					}
				},
				"required": ["path", "checksum"]
			},
			"minItems": 0,
			"uniqueItems": true
		}
	},
	"required": ["performers", "studios", "galleries", "scenes"]
}
```
## performer.json

``` json
{
	"$schema": "http://json-schema.org/draft-07/schema#",
	"$id": "https://github.com/stashapp/stash/wiki/JSON-Specification/performer.json",
	"title": "performer",
	"description": "A json file representing a performer. The file is named by a MD5 Code.",
	"type": "object",
	"properties": {
		"name": {
			"description": "Name of the performer",
			"type": "string"
		},
		"url": {
			"description": "URL to website of the performer",
			"type": "string"
		},
		"twitter": {
			"description": "Twitter name of the performer",
			"type": "string"
		},
		"instagram": {
			"description": "Instagram name of the performer",
			"type": "string"
		},
		"birthdate": {
			"description": "Birthdate of the performer. Format is YYYY-MM-DD",
			"type": "string"
		},
		"ethnicity": {
			"description": "Ethnicity of the Performer. Possible values are black, white, asian or hispanic",
			"type": "string"
		},
		"country": {
			"description": "Country of the performer",
			"type": "string"
		},
		"eye_color": {
			"description": "Eye color of the performer",
			"type": "string"
		},
		"height": {
			"description": "Height of the performer in centimeters",
			"type": "string"
		},
		"measurements": {
			"description": "Measurements of the performer",
			"type": "string"
		},
		"fake_tits": {
			"description": "Whether performer has fake tits. Possible are Yes or No",
			"type": "string"
		},
		"career_length": {
			"description": "The time the performer has been in business. In the format YYYY-YYYY",
			"type": "string"
		},
		"tattoos": {
			"description": "Giving a description of Tattoos of the performer if any",
			"type": "string"
		},
		"piercings": {
			"description": "Giving a description of Piercings of the performer if any",
			"type": "string"
		},
		"image": {
			"description": "Image of the performer, parsed into base64",
			"type": "string"
		},
		"created_at": {
			"description": "The time this performers data was added to the database. Format is YYYY-MM-DDThh:mm:ssTZD",
			"type": "string"
		},
		"updated_at": {
			"description": "The time this performers data was last changed in the database. Format is YYYY-MM-DDThh:mm:ssTZD",
			"type": "string"
		}
	},
	"required": ["name", "ethnicity", "image", "created_at", "updated_at"]
}

```

## studio.json

``` json
{
	"$schema": "http://json-schema.org/draft-07/schema#",
	"$id": "https://github.com/stashapp/stash/wiki/JSON-Specification/studio.json",
	"title": "studio",
	"description": "A json file representing a studio. The file is named by a MD5 Code.",
	"type": "object",
	"properties": {
		"name": {
			"description": "Name of the studio",
			"type": "string"
		},
		"url": {
			"description": "URL to the studios websites",
			"type": "string"
		},
		"image": {
			"description": "Logo of the studio, parsed into base64",
			"type": "string"
		},
		"created_at": {
			"description": "The time this studios data was added to the database. Format is YYYY-MM-DDThh:mm:ssTZD",
			"type": "string"
		},
		"updated_at": {
			"description": "The time this studios data was last changed in the database. Format is YYYY-MM-DDThh:mm:ssTZD",
			"type": "string"
		}
	},
	"required": ["name", "image", "created_at", "updated_at"]
}
```

## scene.json

``` json
{
	"$schema": "http://json-schema.org/draft-07/schema#",
	"$id": "https://github.com/stashapp/stash/wiki/JSON-Specification/scene.json",
	"title": "scene",
	"description": "A json file representing a scene. The file is named by the MD5 Code of the file its data is referring to.",
	"type": "object",
	"properties": {
		"title": {
			"description": "Title of the scene",
			"type": "string"
		},
		"studio": {
			"description": "The name of the studio that produced that scene",
			"type": "string"
		},
		"url": {
			"description": "The url to the scenes original source",
			"type": "string"
		},
		"date": {
			"description": "The release date of the scene. Its given in the format YYYY-MM-DD",
			"type": "string"
		},
		"rating": {
			"description": "The scenes Rating. Its given in stars, from 1 to 5",
			"type": "integer"
		},
		"details": {
			"description": "A description of the scene, containing things like the story arc",
			"type": "string"
		},
		"performers": {
			"description": "A list of names of the performers in this gallery",
			"type": "array",
			"items": {
				"type": "string"
			},
			"minItems": 1,
			"uniqueItems": true
		},
		"tags": {
			"description": "A list of the tags associated with this scene",
			"type": "array",
			"items": {
				"type": "string"
			},
			"minItems": 1,
			"uniqueItems": true
		},
		"markers": {
			"description": "Markers mark certain events in the scene, most often the change of the position. They are attributed with their own tags.",
			"type": "array",
			"items": {
				"type": "object",
				"properties": {
					"title": {
						"description": "Searchable name of the marker",
						"type": "string"
					},
					"seconds": {
						"description": "At what second the marker is set. It is given with after comma values, such as 10.0 or 17.5",
						"type": "string"
					},
					"primary_tag": {
						"description": "A tag identifying this marker. Multiple markers from the same scene with the same primary tag are concatenated, showing them as similar in nature",
						"type": "string"
					},
					"tags": {
						"description": "A list of the tags associated with this marker",
						"type": "array",
						"items": {
							"type": "string"
						},
						"minItems": 1,
						"uniqueItems": true
					},
					"created_at": {
						"description": "The time this marker was added to the database. Format is YYYY-MM-DDThh:mm:ssTZD",
						"type": "string"
					},
					"updated_at": {
						"description": "The time this marker was updated the last time. Format is YYYY-MM-DDThh:mm:ssTZD",
						"type": "string"
					}

				},
				"required": ["seconds", "primary_tag", "created_at", "updated_at"]
			},
			"minItems": 1,
			"uniqueItems": true
		},
		"file": {
			"description": "Some technical data about the scenes file.",
			"type": "object",
			"properties": {
				"size": {
					"description": "The size of the file in bytes",
					"type": "string"
				},
				"duration": {
					"description": "Duration of the scene in seconds. It is given with after comma values, such as 10.0 or 17.5",
					"type": "string"
				},
				"video_codec": {
					"description": "The coding of the video part of the scene file. An example would be h264",
					"type": "string"
				},
				"audio_codec": {
					"description": "The coding of the audio part of the scene file. An example would be aac",
					"type": "string"
				},
				"width": {
					"description": "The width of the scene in pixels",
					"type": "integer"
				},
				"height": {
					"description": "The height of the scene in pixels",
					"type": "integer"
				},
				"framerate": {
					"description": "Framerate of the scene. It is given with after comma values, such as 29.95",
					"type": "string"
				},
				"bitrate": {
					"description": "The bitrate of the video, in bits",
					"type": "integer"
				}

			},
			"required": ["size", "duration", "video_codec", "audio_codec", "height", "width", "framerate", "bitrate"]
		},
		"created_at": {
			"description": "The time this studios data was added to the database. Format is YYYY-MM-DDThh:mm:ssTZD",
			"type": "string"
		},
		"updated_at": {
			"description": "The time this studios data was last changed in the database. Format is YYYY-MM-DDThh:mm:ssTZD",
			"type": "string"
		}
	},
	"required": ["files", "created_at", "updated_at"]
}
```

## gallery.json

No files of this kind are created here yet
```