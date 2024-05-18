python create_coco_tf_record.py --logtostder \
--train_image_dir="./workspace/data/coco/train" \
--val_image_dir="./workspace/data/coco/val" \
--test_image_dir="./workspace/data/coco/test" \
--train_annotations_file="./workspace/data/coco/train/result.json" \
--val_annotations_file="./workspace/data/coco/val/result.json" \
--testdev_annotations_file="./workspace/data/coco/test/result.json" \
--output_dir=./data


PIPELINE_CONFIG_PATH=models/pipeline.config
MODEL_DIR=models/
python object_detection/model_main_tf2.py \
    --pipeline_config_path=${PIPELINE_CONFIG_PATH} \
    --model_dir=${MODEL_DIR} \
    --alsologtostderr