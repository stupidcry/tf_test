python create_coco_tf_record.py --logtostder \
--train_image_dir="./workspace/data/coco/train" \
--val_image_dir="./workspace/data/coco/val" \
--test_image_dir="./workspace/data/coco/test" \
--train_annotations_file="./workspace/data/coco/train/result.json" \
--val_annotations_file="./workspace/data/coco/val/result.json" \
--testdev_annotations_file="./workspace/data/coco/test/result.json" \
--output_dir=./data


python create_pascal_tf_record.py \
    --data_dir=./workspace/data/pascal \
    --output_path=./workspace/data/record \
    --label_map_path=./workspace/data/pascal_label_map.pbtxt

python model_main_tf2.py
  --pipeline_config_path=workspace/data/pascal_label_map.pbtxt
  --model_dir=workspace/models
  --checkpoint_every_n=100
  --num_workers=4
  --alsologtostderr